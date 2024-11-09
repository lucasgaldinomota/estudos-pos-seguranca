# chroot

O comando **`chroot`** (change root) é usado para alterar o diretório raiz de um processo e seus filhos para um diretório especificado. Isso cria um ambiente isolado no qual o processo e seus filhos "veem" apenas o conteúdo dentro desse diretório, como se fosse a raiz do sistema de arquivos. Esse ambiente isolado é chamado de **"chroot jail"**.

### Funcionamento do `chroot`:
- Quando você executa o `chroot`, ele altera o diretório raiz ("/") do sistema de arquivos do processo para o diretório especificado.
- Esse processo e seus filhos não têm acesso ao sistema de arquivos fora do novo diretório raiz, o que cria uma forma de isolamento.

### Sintaxe básica:
```bash
chroot /diretorio
```

### Exemplo básico:
Suponha que você tenha um diretório chamado `/mnt/root` que contém uma estrutura de sistema de arquivos. Você pode "prender" um processo dentro desse diretório com o seguinte comando:

```bash
sudo chroot /mnt/root
```

Isso fará com que o sistema dentro de `/mnt/root` seja tratado como o sistema de arquivos raiz para o processo que está sendo executado.

### Usos Comuns de `chroot`:

1. **Ambiente de Recuperação**:
   - O `chroot` é frequentemente usado em situações de recuperação do sistema. Por exemplo, se o sistema não inicializar corretamente, você pode inicializar a partir de um live CD ou dispositivo USB e usar `chroot` para acessar o sistema de arquivos danificado e reparar arquivos ou configurações.
   
2. **Isolamento de Processos**:
   - É usado para isolar processos, como um método para criar um "sandbox" em que o processo não pode acessar recursos fora de um diretório específico.
   
3. **Compilar ou Executar Software em um Ambiente Controlado**:
   - Ao usar `chroot`, você pode criar um ambiente controlado para compilar software ou executar programas, como se fosse um sistema diferente.
   
4. **Recuperação de Senha**:
   - Pode ser usado para redefinir senhas de usuários no sistema se você tiver acesso root e o sistema estiver montado em um ponto de recuperação.
   
### Exemplo de Ambiente de Recuperação:

Imagine que você tenha um sistema que não inicializa, mas deseja reparar os arquivos do sistema. Suponha que o sistema de arquivos esteja montado em `/mnt` e você deseja acessar o ambiente de chroot:

1. Monte o sistema de arquivos:
   ```bash
   sudo mount /dev/sdX1 /mnt
   ```

2. Chroot no diretório:
   ```bash
   sudo chroot /mnt
   ```

Agora, você está efetivamente dentro do sistema como se fosse o sistema raiz, permitindo que você edite arquivos e execute comandos para reparar o sistema.

### Limitações do `chroot`:
- O `chroot` não oferece segurança robusta, pois um processo dentro do chroot pode, teoricamente, escapar do ambiente com privilégios adequados (por exemplo, usando técnicas de exploração).
- Não oferece isolamento completo como containers ou máquinas virtuais.

### Alternativas ao `chroot`:
Para um isolamento mais seguro, soluções como **containers Docker** ou **máquinas virtuais** são mais apropriadas, pois proporcionam uma separação mais rigorosa entre o processo e o sistema host.