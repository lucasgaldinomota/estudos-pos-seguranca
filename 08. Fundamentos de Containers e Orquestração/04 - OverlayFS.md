# OverlayFS

**OverlayFS** é um sistema de arquivos do tipo "union" no Linux, que permite que dois sistemas de arquivos sejam combinados em um único sistema de arquivos, como se fossem uma única unidade. Ele é amplamente usado em contêineres, como no Docker, para criar camadas (layers) de arquivos que podem ser sobrepostas e modificadas de forma eficiente.

### Como o OverlayFS Funciona

O OverlayFS permite a combinação de dois sistemas de arquivos:
- **Lower layer** (camada inferior): É o sistema de arquivos de leitura. Normalmente, ele contém arquivos que são "somente leitura" ou que não mudam frequentemente.
- **Upper layer** (camada superior): É o sistema de arquivos de leitura e gravação, onde as alterações e arquivos novos são armazenados.

Quando você acessa arquivos no OverlayFS, ele "sobrepõe" a camada superior à camada inferior. Se o arquivo existir na camada superior, ele é acessado diretamente dessa camada. Se não existir, o sistema irá buscar na camada inferior.

### Componentes Principais:
- **Lower directory (diretório inferior)**: Contém arquivos que são compartilhados entre várias instâncias, geralmente estáticos ou de leitura.
- **Upper directory (diretório superior)**: Contém arquivos modificados ou novos. Qualquer modificação é feita nesta camada.
- **Merged directory (diretório mesclado)**: O diretório onde as duas camadas são combinadas (mescladas). Esse diretório é onde os arquivos finais são acessados.

### Benefícios do OverlayFS:
1. **Eficiência**: OverlayFS é eficiente em termos de uso de espaço porque evita duplicação de dados. Os arquivos que não são modificados permanecem na camada inferior, enquanto as modificações são armazenadas apenas na camada superior.
2. **Rápido**: Ele é muito rápido para operações de leitura, já que arquivos não modificados são lidos diretamente da camada inferior, sem necessidade de duplicação.
3. **Economia de Armazenamento**: Como os arquivos que não são alterados são compartilhados, ele reduz a necessidade de armazenamento adicional.
4. **Ideal para Contêineres**: É amplamente utilizado em contêineres Docker e outras tecnologias de contêinerização, pois permite criar imagens leves e eficientes com várias camadas.

### Como funciona o OverlayFS:
- Se um arquivo é modificado, o sistema cria uma cópia desse arquivo na camada superior. A camada inferior permanece intacta.
- Se um arquivo é excluído, o sistema usa uma técnica chamada **"whiteout"** para mascarar o arquivo na camada inferior, sem realmente apagá-lo.
- O sistema apresenta uma visão unificada, onde os arquivos são lidos de uma camada ou de outra, dependendo se são modificados ou não.

### Exemplo Prático com Docker:
No Docker, o OverlayFS é utilizado para gerenciar as **imagens** de contêineres. Cada imagem é composta de várias camadas. Quando um contêiner é iniciado, ele utiliza essas camadas para criar um sistema de arquivos unificado. Isso significa que:
- **Camadas base** (como uma imagem do sistema operacional) são compartilhadas entre diferentes contêineres.
- **Modificações feitas no contêiner** (como instalação de novos pacotes) acontecem na camada superior, sem alterar as camadas base.

### Exemplo de Comando para Montar um OverlayFS:
Para criar um sistema de arquivos Overlay, você pode usar o comando `mount` no Linux:

```bash
sudo mount -t overlay overlay -o lowerdir=/path/to/lower,upperdir=/path/to/upper,workdir=/path/to/work /path/to/merged
```

- `lowerdir`: A camada inferior (sistema de arquivos somente leitura).
- `upperdir`: A camada superior (sistema de arquivos de leitura e gravação).
- `workdir`: Um diretório de trabalho necessário para operações de escrita (criação de arquivos, exclusões, etc.).
- `merged`: O diretório onde o sistema de arquivos unificado será montado.

### Diferença entre OverlayFS e UnionFS:
**UnionFS** e **OverlayFS** são tecnologias similares, mas OverlayFS é mais recente e geralmente considerado mais rápido e mais eficiente, já que foi projetado com melhorias específicas para o kernel Linux e uso em contêineres. O UnionFS, por outro lado, foi uma implementação anterior e tem mais limitações de desempenho e compatibilidade.

### Uso em Contêineres:
- **Docker** e outros sistemas de contêinerização utilizam OverlayFS para criar camadas de imagens de contêiner. O sistema de arquivos Overlay ajuda a economizar espaço em disco e a melhorar o desempenho, tornando-o uma solução popular para ambientes de contêineres.