---
title: 'Tutorial: Instale e use ferramentas locais do .NET Core'
description: Saiba como instalar e usar uma ferramenta .NET como ferramenta local.
ms.date: 02/12/2020
ms.openlocfilehash: a4355886513040e2436bdbd87905e5baee2dd7a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156693"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a>Tutorial: Instale e use uma ferramenta local .NET Core usando o .NET Core CLI

**Este artigo se aplica a:** ✔️ .NET Core 3.0 SDK e versões posteriores

Este tutorial ensina como instalar e usar uma ferramenta local. Você usa uma ferramenta que você cria no [primeiro tutorial desta série](global-tools-how-to-create.md).

## <a name="prerequisites"></a>Pré-requisitos

* Complete o [primeiro tutorial desta série.](global-tools-how-to-create.md)
* Instale o tempo de execução do .NET Core 2.1.

  Para este tutorial você instala e usa uma ferramenta que tem como alvo o .NET Core 2.1, então você precisa ter esse tempo de execução instalado em sua máquina. Para instalar o tempo de execução 2.1, acesse a [página de download do .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1) e encontre o link de instalação em tempo de execução na coluna Executar aplicativos - **Runtime.**

## <a name="create-a-manifest-file"></a>Criar um arquivo manifesto

Para instalar uma ferramenta apenas para acesso local (para o diretório atual e subdiretórios), ele precisa ser adicionado a um arquivo manifesto.

A partir da pasta *microsoft.botsay,* navegue até um nível até a pasta do *repositório:*

```console
cd ..
```

Crie um arquivo manifesto executando o novo comando [dotnet:](dotnet-new.md)

```dotnetcli
dotnet new tool-manifest
```

A saída indica criação bem sucedida do arquivo.

```console
The template "Dotnet local tool manifest file" was created successfully.
```

O arquivo *.config/dotnet-tools.json* ainda não tem ferramentas:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

As ferramentas listadas em um arquivo manifesto estão disponíveis para o diretório e subdiretórios atuais. O diretório atual é aquele que contém o diretório *.config* com o arquivo manifesto.

Quando você usa um comando CLI que se refere a uma ferramenta local, o SDK procura um arquivo manifesto no diretório atual e diretórios-pai. Se ele encontrar um arquivo manifesto, mas o arquivo não incluir a ferramenta referenciada, ele continuará a pesquisa através de diretórios-mãe. A pesquisa termina quando encontra a ferramenta referenciada `isRoot` ou `true`encontra um arquivo manifesto com set para .

## <a name="install-botsay-as-a-local-tool"></a>Instale o botsay como uma ferramenta local

Instale a ferramenta a partir do pacote que você criou no primeiro tutorial:

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

Este comando adiciona a ferramenta ao arquivo manifesto que você criou na etapa anterior. A saída de comando mostra em qual arquivo manifesto a ferramenta recém-instalada está em:

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

O arquivo *.config/dotnet-tools.json* agora tem uma ferramenta:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "microsoft.botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a>Usar a ferramenta

Invoque a `dotnet tool run` ferramenta executando o comando da pasta do *repositório:*

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a>Restaurar uma ferramenta local instalada por outros

Você normalmente instala uma ferramenta local no diretório raiz do repositório. Depois de verificar o arquivo manifesto no repositório, outros desenvolvedores podem obter o arquivo manifesto mais recente. Para instalar todas as ferramentas listadas no arquivo `dotnet tool restore` manifesto, eles podem executar um único comando.

1. Abra o arquivo *.config/dotnet-tools.json* e substitua o conteúdo pelo seguinte JSON:

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "microsoft.botsay": {
         "version": "1.0.0",
         "commands": [
           "botsay"
         ]
       },
       "dotnetsay": {
         "version": "2.1.3",
         "commands": [
           "dotnetsay"
         ]
       }
     }
   }
   ```

1. Substitua pelo `<name>` nome usado para criar o projeto.

1. Salve suas alterações.

   Fazer essa alteração é o mesmo que obter a versão mais recente `dotnetsay` do repositório depois que outra pessoa instalou o pacote para o diretório do projeto.

1. Execute o comando `dotnet tool restore`.

   ```dotnetcli
   dotnet tool restore
   ```

   O comando produz saída como o seguinte exemplo:

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. Verifique se as ferramentas estão disponíveis:

   ```dotnetcli
   dotnet tool list
   ```

   A saída é uma lista de pacotes e comandos, semelhante ao seguinte exemplo:

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. Teste as ferramentas:

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a>Atualize uma ferramenta local

A versão instalada da `dotnetsay` ferramenta local é 2.1.3.  A versão mais recente é 2.1.4. Use o comando [dotnet tool update](dotnet-tool-update.md) para atualizar a ferramenta para a versão mais recente.

```dotnetcli
dotnet tool update dotnetsay
```

A saída indica o novo número da versão:

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

O comando update encontra o primeiro arquivo manifesto que contém o ID do pacote e o atualiza. Se não houver tal ID de pacote em qualquer arquivo manifesto que esteja no escopo da pesquisa, o SDK adiciona uma nova entrada ao arquivo manifesto mais próximo. O escopo de pesquisa é através de `isRoot = true` diretórios-mãe até que um arquivo manifesto seja encontrado.

## <a name="remove-local-tools"></a>Remover ferramentas locais

Remova as ferramentas instaladas executando o comando [de desinstalar a ferramenta dotnet:](dotnet-tool-uninstall.md)

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a>Solucionar problemas

Se você receber uma mensagem de erro ao seguir o tutorial, consulte [Problemas de uso da ferramenta .NET Core](troubleshoot-usage-issues.md).

## <a name="see-also"></a>Confira também

Para obter mais informações, consulte [as ferramentas .NET Core](global-tools.md)
