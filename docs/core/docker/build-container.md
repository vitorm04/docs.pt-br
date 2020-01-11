---
title: 'Tutorial: Colocar em contêiner um aplicativo com o Docker'
description: Neste tutorial, você aprenderá a colocar em contêiner um aplicativo .NET Core com o Docker.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 17d3dfbe58770b19a75be1dad3ae03406584992c
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900107"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Tutorial: colocar um aplicativo .NET Core em contêineres

Este tutorial ensina como criar uma imagem do Docker que contenha seu aplicativo .NET Core. A imagem pode ser usada para criar contêineres para seu ambiente de desenvolvimento local, nuvem privada ou nuvem pública.

Você aprenderá a:

> [!div class="checklist"]
>
> - Criar e publicar um aplicativo .NET Core simples
> - Criar e configurar um Dockerfile para .NET Core
> - Criar uma imagem do Docker
> - Criar e executar um contêiner do Docker

Você aprenderá as tarefas de build e implantação de contêiner do Docker para um aplicativo .NET Core. A *plataforma Docker* usa o *Mecanismo do Docker* para criar e empacotar aplicativos como *imagens do Docker* com agilidade. Essas imagens são gravadas no formato *Dockerfile* para serem implantadas e executadas em um contêiner em camadas.

> [!TIP]
> Se você estiver trabalhando com um aplicativo de ASP.NET Core existente, consulte o tutorial [saiba como colocar um aplicativo em contêineres de ASP.NET Core](/aspnet/core/host-and-deploy/docker/building-net-docker-images) .

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

Instale os seguintes pré-requisitos:

- [SDK do .NET Core 3,1](https://dotnet.microsoft.com/download)\
Se você tiver o .NET Core instalado, use o comando `dotnet --info` para determinar qual SDK está usando.

- [Docker Community Edition](https://www.docker.com/products/docker-desktop)

- Uma pasta de trabalho temporária para o *Dockerfile* e o aplicativo de exemplo do .NET Core. Neste tutorial, o nome *Docker – Working* é usado como a pasta de trabalho.

## <a name="create-net-core-app"></a>Criar um aplicativo .NET Core

Você precisa de um aplicativo .NET Core que o contêiner do Docker irá executar. Abra seu terminal, crie uma pasta de trabalho se você ainda não fez isso e entre nela. Na pasta de trabalho, execute o seguinte comando para criar um novo projeto em um subdiretório chamado *app*:

```dotnetcli
dotnet new console -o app -n myapp
```

A árvore de pastas terá aparência semelhante à seguinte:

```
docker-working
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.dgspec.json
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

O comando `dotnet new` cria uma pasta chamada *app* e gera um aplicativo "Olá, Mundo". Entre na pasta *app* e execute o comando `dotnet run`. Você verá a seguinte saída:

```console
> dotnet run
Hello World!
```

O modelo padrão cria um aplicativo que imprime no terminal e, em seguida, sai. Neste tutorial, você usará um aplicativo que faz um loop indefinidamente. Abra o arquivo *Program.cs* em um editor de texto. Ele deve se parecer com o seguinte código:

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Substitua o arquivo pelo seguinte código que conta os números a cada segundo:

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

Salve o arquivo e teste o programa novamente com `dotnet run`. Lembre-se de que esse aplicativo é executado indefinidamente. Use o comando Cancel <kbd>CTRL</kbd>+<kbd>C</kbd> para interrompê-lo. Você verá a seguinte saída:

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Se você passar um número na linha de comando para o aplicativo, ele apenas contará até tal valor e, em seguida, sairá. Experimente com `dotnet run -- 5` para contar até cinco.

> [!NOTE]
> Quaisquer parâmetros após `--` não são passados para o comando `dotnet run` e, em vez disso, são passados para o aplicativo.

## <a name="publish-net-core-app"></a>Publicar um aplicativo .NET Core

Antes de adicionar seu aplicativo .NET Core à imagem do Docker, publique-o. Você deseja assegurar que o contêiner execute a versão publicada do aplicativo quando ele for iniciado.

Da pasta de trabalho, entre na pasta *app* com o código-fonte de exemplo e execute o seguinte comando:

```dotnetcli
dotnet publish -c Release
```

Esse comando compila seu aplicativo para a pasta *publish*. O caminho para a pasta *publish* da pasta de trabalho deve ser `.\app\bin\Release\netcoreapp3.1\publish\`

Na pasta do *aplicativo* , obtenha uma listagem de diretório da pasta de publicação para verificar se o arquivo *MyApp. dll* foi criado. 

```console
> dir bin\Release\netcoreapp3.1\publish

    Directory:  C:\docker-working\app\bin\Release\netcoreapp3.1\publish

01/09/2020  11:41 AM    <DIR>          .
01/09/2020  11:41 AM    <DIR>          ..
01/09/2020  11:41 AM               407 myapp.deps.json
01/09/2020  12:15 PM             4,608 myapp.dll
01/09/2020  12:15 PM           169,984 myapp.exe
01/09/2020  12:15 PM               736 myapp.pdb
01/09/2020  11:41 AM               154 myapp.runtimeconfig.json
```

Se você estiver usando o Linux ou o macOS, use o comando `ls` para obter uma listagem de diretório e verificar se o arquivo *MyApp. dll* foi criado.

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a>Criar o Dockerfile

O arquivo *Dockerfile* é usado pelo comando `docker build` para criar uma imagem de contêiner. Esse arquivo é um arquivo de texto chamado *Dockerfile* que não tem uma extensão.

No terminal, navegue em um diretório acima até a pasta de trabalho criada no início. Crie um arquivo chamado *Dockerfile* em sua pasta de trabalho e abra-o em um editor de texto. Dependendo do tipo de aplicativo que você pretende colocar em contêiner, você escolherá o tempo de execução do ASP.NET Core ou o tempo de execução do .NET Core. Em caso de dúvida, escolha o tempo de execução de ASP.NET Core, que inclui o tempo de execução do .NET Core. Este tutorial usará a imagem ASP.NET Core Runtime, mas o aplicativo criado nas seções anteriores é um aplicativo .NET Core.

- Tempo de execução ASP.NET Core

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- runtime do .NET Core

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

O comando `FROM` informa ao Docker para efetuar pull da imagem marcada **3,1** do repositório especificado. Certifique-se de extrair a versão de tempo de execução que corresponde ao tempo de execução direcionado pelo seu SDK. Por exemplo, o aplicativo criado na seção anterior usava o SDK do .NET Core 3,1 e a imagem base mencionada no *Dockerfile* é marcada com **3,1**.

Salve o arquivo *Dockerfile*. A estrutura de diretório da pasta de trabalho deve ser semelhante à mostrada a seguir. Algumas das pastas e arquivos de nível mais profundo foram eliminados para economizar espaço no artigo:

```
docker-working
│   Dockerfile
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp3.1
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.exe
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

Do terminal, execute o seguinte comando:

```console
docker build -t myimage -f Dockerfile .
```

O Docker processará cada linha no *Dockerfile*. O `.` no comando `docker build` instrui o Docker a usar a pasta atual para encontrar um *Dockerfile*. Esse comando constrói a imagem e cria um repositório local chamado **myimage** que aponta para essa imagem. Após a conclusão desse comando, execute `docker images` para ver uma lista de imagens instaladas:

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

Observe que as duas imagens compartilham o mesmo valor de **ID DA IMAGEM**. O valor é o mesmo entre as duas imagens porque o único comando no *Dockerfile* era basear a nova imagem em uma imagem existente. Vamos adicionar dois comandos ao *Dockerfile*. Cada comando cria uma nova camada de imagem com o comando final que representa a imagem à qual a entrada do repositório **MyImage** aponta.

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

O comando `COPY` informa ao Docker para copiar a pasta especificada em seu computador para uma pasta no contêiner. Nesse exemplo, a pasta *publish* é copiada para uma pasta chamada *app* no contêiner.

O comando seguinte, `ENTRYPOINT`, informa ao Docker para configurar o contêiner para ser executado como um executável. Quando o contêiner é iniciado, o comando `ENTRYPOINT` é executado. Quando esse comando terminar, o contêiner será interrompido automaticamente.

No seu terminal, execute `docker build -t myimage -f Dockerfile .` e, quando o comando terminar, execute `docker images`.

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  1.624MB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> 38db0eb8f648
Step 2/3 : COPY app/bin/Release/netcoreapp3.1/publish/ app/
 ---> 37873673e468
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in d8deb7b3aa9e
Removing intermediate container d8deb7b3aa9e
 ---> 0d602ca35c1d
Successfully built 0d602ca35c1d
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              0d602ca35c1d        4 seconds ago       346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

Cada comando no *Dockerfile* gerou uma camada e criou uma **ID DA IMAGEM**. A **ID DA IMAGEM** final (a sua será diferente) é **ddcc6646461b** e, a seguir, você criará um contêiner baseado nessa imagem.

## <a name="create-a-container"></a>Criar um contêiner

Agora que você tem uma imagem que contém o seu aplicativo, você pode criar um contêiner. Você pode criar um contêiner de duas maneiras. Primeiro, criar um novo contêiner que foi interrompido.

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

O comando `docker create` acima criará um contêiner baseado na imagem **myimage**. A saída desse comando mostra a **ID DO CONTÊINER** (a sua será diferente) do contêiner criado. Para ver uma lista de *todos* os contêineres, use o comando `docker ps -a`:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a>Gerenciar o contêiner

Cada contêiner é atribuído a um nome aleatório que você pode usar para se referir a essa instância de contêiner. Por exemplo, o contêiner criado automaticamente escolhe o nome **gallant_lehmann** (o seu será diferente) e esse nome pode ser usado para iniciar o contêiner. Você substitui o nome automático por um específico usando o parâmetro `docker create --name`.

O exemplo a seguir usa o comando `docker start` para iniciar o contêiner e, em seguida, usa o comando `docker ps` para mostrar apenas os contêineres em execução:

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

Da mesma forma, o comando `docker stop` interromperá o contêiner. O exemplo a seguir usa o comando `docker stop` para parar o contêiner e, em seguida, usa o comando `docker ps` para mostrar que nenhum contêiner está em execução:

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a>Conectar-se a um contêiner

Depois que um contêiner estiver em execução, você poderá se conectar a ele para ver a saída. Use os comandos `docker start` e `docker attach` para iniciar o contêiner e inspecionar o fluxo de saída. Neste exemplo, a tecla <kbd>Ctrl + C</kbd> é usada para desanexar do contêiner em execução. Esse pressionamento de teclas pode, na verdade, encerrar o processo no contêiner, o que interromperá o contêiner. O parâmetro `--sig-proxy=false` garante que <kbd>Ctrl+C</kbd> não interrompa o processo no contêiner.

Depois de desanexar do contêiner, reanexe para verificar se ele ainda está em execução e contando.

```console
> docker start gallant_lehmann
gallant_lehmann

> docker attach --sig-proxy=false gallant_lehmann
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false gallant_lehmann
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a>Criar um contêiner

Para os fins desse artigo, você não quer contêineres sem função alguma. Exclua o contêiner que você criou anteriormente. Se o contêiner estiver em execução, interrompa-o.

```console
> docker stop gallant_lehmann
```

O exemplo a seguir lista todos os contêineres. Em seguida, ele usa o comando `docker rm` para excluir o contêiner e, em seguida, verifica uma segunda vez para verificar qualquer contêiner em execução.

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a>Execução única

O Docker fornece o comando `docker run` para criar e executar o contêiner como um único comando. Este comando elimina a necessidade de executar `docker create` e, em seguida, `docker start`. Você também pode definir esse comando para excluir automaticamente o contêiner quando o contêiner for interrompido. Por exemplo, use `docker run -it --rm` para fazer duas coisas: primeiro, use automaticamente o terminal atual para se conectar ao contêiner e, quando o contêiner terminar, remova-o:

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

Com `docker run -it`, o comando <kbd>Ctrl+C</kbd> interromperá o processo em execução no contêiner, que, por sua vez, interrompe o contêiner. Como o parâmetro `--rm` foi fornecido, o contêiner é automaticamente excluído quando o processo é interrompido. Verifique se ele não existe:

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a>Alterar o ENTRYPOINT

O comando `docker run` também permite modificar o comando `ENTRYPOINT` do *Dockerfile* e executar outra coisa, mas apenas para esse contêiner. Por exemplo, use o seguinte comando para executar `bash` ou `cmd.exe`. Edite o comando conforme necessário.

#### <a name="windows"></a>Portal

Neste exemplo, `ENTRYPOINT` é alterado para `cmd.exe`. <kbd>CTRL</kbd>+<kbd>C</kbd> é pressionado para encerrar o processo e parar o contêiner.

```console
> docker run -it --rm --entrypoint "cmd.exe" myimage

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a>Linux

Neste exemplo, `ENTRYPOINT` é alterado para `bash`. O comando `quit` é executado, o que encerra o processo e interrompe o contêiner.

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a>Comandos essenciais

O Docker tem muitos comandos diferentes que englobam o que você deseja fazer com o contêiner e as imagens. Esses comandos do Docker são essenciais para gerenciar seus contêineres:

- [docker build](https://docs.docker.com/engine/reference/commandline/build/)
- [docker run](https://docs.docker.com/engine/reference/commandline/run/)
- [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
- [docker stop](https://docs.docker.com/engine/reference/commandline/stop/)
- [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
- [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
- [docker image](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Limpar recursos

Durante este tutorial, você criou contêineres e imagens. Se quiser, exclua esses recursos. Use os seguintes comandos para:

01. Listar todos os contêineres

    ```console
    > docker ps -a
    ```

02. Interromper os contêineres em execução. `CONTAINER_NAME` representa o nome atribuído automaticamente ao contêiner.

    ```console
    > docker stop CONTAINER_NAME
    ```

03. Excluir o contêiner

    ```console
    > docker rm CONTAINER_NAME
    ```

Em seguida, exclua todas as imagens que você não deseja mais em seu computador. Exclua a imagem criada pelo seu *Dockerfile* e exclua a imagem do .NET Core na qual o *Dockerfile* teve base. Você pode usar a **ID DA IMAGEM** ou a cadeia de caracteres formatada **REPOSITÓRIO:TAG**.

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

Use o comando `docker images` para ver uma lista de imagens instaladas.

> [!NOTE]
> Arquivos de imagem podem ser grandes. Normalmente, você removeria contêineres temporários criados durante o teste e o desenvolvimento de seu aplicativo. Em geral, mantenha as imagens de base com o runtime instalado se você planeja construir outras imagens com base nesse runtime.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

- [Aprenda a colocar em contêiner um aplicativo ASP.NET Core.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [Experimentar o Tutorial de Microsserviço do ASP.NET Core.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Revisar os serviços do Azure que oferecem suporte a contêineres.](https://azure.microsoft.com/overview/containers/)
- [Ler mais sobre os comandos do Dockerfile.](https://docs.docker.com/engine/reference/builder/)
- [Explore as Ferramentas de Contêiner para Visual Studio](/visualstudio/containers/overview)
