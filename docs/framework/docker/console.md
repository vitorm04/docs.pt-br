---
title: Executando aplicativos de console no Docker
description: "Saiba como selecionar um aplicativo de console do .NET Framework e executá-lo em um contêiner do Docker do Windows."
author: spboyer
keywords: ".NET, contêiner, console, aplicativos"
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.translationtype: Human Translation
ms.sourcegitcommit: 890c058bd09893c2adb185e1d8107246eef2e20a
ms.openlocfilehash: 4f1034763e4dae3711694b441b7a64b40cc99456
ms.contentlocale: pt-br
ms.lasthandoff: 04/18/2017

---

# <a name="running-console-applications-in-windows-containers"></a>Executando aplicativos de console em contêineres do Windows

Aplicativos de console são usados para várias finalidades, desde consultas de status a tarefas de execução longa de processamento de imagens de documentos. Em qualquer caso, a capacidade de inicializar e dimensionar esses aplicativos apresenta limitações de aquisições de hardware, tempos de inicialização ou execução de várias instâncias.

Mover seus aplicativos de console para usar contêineres do Docker e do Windows Server permite iniciar esses aplicativos de um estado limpo, permitindo que eles realizem a operação e desliguem corretamente. Este tópico mostra as etapas necessárias para mover um aplicativo de console para um contêiner baseado no Windows e inicializá-lo usando um script do PowerShell.

O aplicativo de console de exemplo é um exemplo simples que usa um argumento, neste caso uma pergunta e retorna uma resposta aleatória. Isso pode pegar um `customer_id` e processar seus impostos ou criar uma miniatura para um argumento `image_url`.

Além da resposta, `Environment.MachineName` foi adicionado à resposta para mostrar a diferença entre executar o aplicativo localmente e em um contêiner do Windows. Ao executar o aplicativo localmente, o nome do computador local deve ser retornado e, ao executar em um contêiner do Windows, a ID da sessão do contêiner é retornada.

O [exemplo completo](https://github.com/dotnet/docs/tree/master/samples/framework/docker/ConsoleRandomAnswerGenerator) está disponível no repositório de documentos/dotnet no GitHub. Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Você precisa estar familiarizado com alguns termos do Docker antes de começar a mover seu aplicativo para um contêiner.

> Uma *imagem do Docker* é um modelo de somente leitura que define o ambiente para um contêiner em execução, incluindo o SO (sistema operacional), os componentes do sistema e os aplicativos.

Um recurso importante das imagens do Docker é que elas são compostas de uma imagem de base. Cada nova imagem adiciona um pequeno conjunto de recursos a uma imagem existente. 

> Um *contêiner do Docker* é uma instância em execução de uma imagem. 

Você dimensiona um aplicativo executando a mesma imagem em vários contêineres.
Conceitualmente, isso é semelhante a executar o mesmo aplicativo em vários hosts.

Você pode aprender mais sobre a arquitetura do Docker lendo [Docker Overview](https://docs.docker.com/engine/understanding-docker/) (Visão geral do Docker) no site do Docker. 

Mover seu aplicativo de console demanda somente algumas etapas.

1. [Compilar o aplicativo](#building-the-application)
1. [Criar um Dockerfile para a imagem](#creating-the-dockerfile)
1. [Processo para compilar e executar o contêiner do Docker](#creating-the-image)

## <a name="prerequisites"></a>Pré-requisitos
Contêineres do Windows têm suporte na [Atualização de Aniversário do Windows 10](https://www.microsoft.com/en-us/software-download/windows10/) ou no [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).

> [!NOTE]
>Se estiver usando o Windows Server 2016, você deve habilitar os contêineres manualmente, uma vez que o instalador do Docker para Windows não habilitará o recurso. Verifique se todas as atualizações foram executados para o sistema operacional e siga as instruções no artigo [Implantação de host de contêiner](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment) para instalar os recursos de Docker e os contêineres.

Você precisa ter o Docker para Windows, na versão 1.12 Beta 26 ou superior, para dar suporte a contêineres do Windows. Por padrão, o Docker habilita contêineres baseados em Linux. Alterne para contêineres do Windows clicando com o botão direito do mouse no ícone do Docker na bandeja do sistema e selecione **Alternar para contêineres do Windows**. O Docker executará o processo de alteração e talvez seja necessário reiniciar.

![Contêineres do Windows](./media/console/SwitchContainer.png)

## <a name="building-the-application"></a>Compilando o aplicativo
Normalmente, os aplicativos de console são distribuídos por meio de um instalador, FTP ou implantação de Compartilhamento de arquivos. Durante a implantação em um contêiner, os ativos precisam ser compilados e preparados em um local que possa ser usado quando a imagem do Docker for criada.

Em *build.ps1*, o script usa [MSBuild](https://msdn.microsoft.com/library/dd393574.aspx) para compilar o aplicativo para concluir a tarefa de criação de ativos. Alguns parâmetros são passados para o MSBuild para finalizar os ativos necessários. O nome do arquivo de projeto ou solução a ser compilada, o local de saída e a configuração (versão ou depuração).

Na chamada para `Invoke-MSBuild`, `OutputPath` é definido como **publish** e `Configuration` é definido como **Release**. 

```
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj /p:OutputPath=.\publish /p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a>Criando o Dockerfile
A imagem base usada para um aplicativo de console do .NET Framework é `microsoft/windowsservercore`, disponível publicamente no [Hub do Docker](https://hub.docker.com/r/microsoft/windowsservercore/). A imagem base contém uma instalação mínima do Windows Server 2016, o .NET Framework 4.6.2 e serve como a imagem base do sistema operacional para contêineres do Windows.

```
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```
A primeira linha no Dockerfile designa a imagem base usando a instrução [`FROM`](https://docs.docker.com/engine/reference/builder/#/from). Em seguida, [`ADD`](https://docs.docker.com/engine/reference/builder/#/add) no arquivo copia os ativos do aplicativo da pasta **publish** para a pasta raiz do contêiner. Definir o [`ENTRYPOINT`](https://docs.docker.com/engine/reference/builder/#/entrypoint) da imagem afirma que este é o comando ou o aplicativo que será executado quando o contêiner for iniciado. 

## <a name="creating-the-image"></a>Criando a imagem
Para criar a imagem do Docker, o código a seguir é adicionado ao script *build.ps1*. Quando o script é executado, a imagem `console-random-answer-generator` é criada usando os ativos compilados do MSBuild definido na seção [Compilando o aplicativo](#building-the-application).

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

Execute o script usando `.\build.ps1` no prompt de comando do PowerShell.

Quando a compilação estiver concluída, usando o comando `docker images` de uma linha de comando ou o prompt do PowerShell você verá que a imagem foi criada e está pronta para ser executada.

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a>Executando o contêiner
Você pode iniciar o contêiner da linha de comando usando os comandos do Docker.

```
docker run console-random-answer-generator "Are you a square container?"
```

A saída é

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

Se executar o comando `docker ps -a` do PowerShell, você pode ver que o contêiner ainda existe.

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS                          
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago      
```

A coluna STATUS mostra que "Há cerca de um minuto" o aplicativo foi concluído e pode ser desligado. Se o comando fosse executado cem vezes, haveria uma centena de contêineres estáticos sem nenhum trabalho a fazer. No cenário inicial, a operação ideal seria realizar o trabalho e, depois, desligamento ou limpeza. Para realizar esse fluxo de trabalho, adicionar a opção `--rm` ao comando `docker run` removerá o contêiner assim que o sinal `Exited` for recebido.

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

Ao executar o comando com essa opção e examinar a saída do comando `docker ps -a`, observe que a ID do contêiner (o `Environment.MachineName`) não está na lista.

### <a name="running-the-container-using-powershell"></a>Executando o contêiner usando o PowerShell
Nos arquivos de projeto de exemplo, também há um *run.ps1*, que é um exemplo de como usar o PowerShell para executar o aplicativo aceitando os argumentos.

Para executar, abra o PowerShell e use o seguinte comando:

```
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a>Resumo
Apenas adicionando um Dockerfile e publicando o aplicativo, você pode dispor em contêineres seus aplicativos de console do .NET Framework e, então, tirar proveito da execução de várias instâncias, de iniciar e parar de maneira limpa e de mais recursos do Windows Server 2016 sem fazer nenhuma alteração ao código do aplicativo em todos os.

