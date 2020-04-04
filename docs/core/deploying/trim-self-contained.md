---
title: Aparar aplicações independentes
description: Aprenda a aparar aplicativos autônomos para reduzir seu tamanho. O .NET Core empacota o tempo de execução com um aplicativo que é publicado independente mente e geralmente inclui mais tempo de execução do que é necessário.
author: jamshedd
ms.author: jamshedd
ms.date: 01/23/2020
ms.openlocfilehash: 5206ca255c500b382402ac4e7dd3300b7face1cf
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665631"
---
# <a name="trim-self-contained-deployments-and-executables"></a>Apare implantações e executáveis autônomos

Ao publicar um aplicativo independente, o tempo de execução do .NET Core é empacotado com o aplicativo. Este agrupamento adiciona uma quantidade significativa de conteúdo ao seu aplicativo embalado.

Quando se trata de implantar seu aplicativo, o tamanho muitas vezes é um fator importante. Manter o tamanho do aplicativo do pacote o menor possível é tipicamente uma meta para os desenvolvedores de aplicativos.

Dependendo da complexidade do aplicativo, apenas um subconjunto do tempo de execução é necessário para executar o aplicativo. Estas partes não utilizadas do tempo de execução são desnecessárias e podem ser cortadas da aplicação embalada.

> [!NOTE]
> Trimming é um recurso experimental no .NET Core 3.1 e _só_ está disponível para aplicativos que são publicados independentes.

## <a name="trim-your-application"></a>Apare sua aplicação

O exemplo a seguir mostra como aparar seu aplicativo usando o comando [dotnet publish:](../tools/dotnet-publish.md)

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true /p:PublishSingleFile=false /p:PublishTrimmed=true
```

O recurso de corte funciona examinando os binários de aplicativos para descobrir e construir um gráfico dos conjuntos de tempo de execução necessários. As montagens restantes de tempo de execução que não são referenciadas são aparadas.

## <a name="trimming-issues-when-using-reflection"></a>Questões de corte ao usar reflexão

Existem cenários em que a funcionalidade de corte falhará em detectar referências. Por exemplo, um aplicativo que usa reflexão pode esbarrar nessa questão porque a dependência do conjunto só será conhecida em tempo de execução.

O corte só é um problema se o uso do reflexo depender de um conjunto de tempo de execução que não seja referenciado diretamente. Tenha em mente que seu código de aplicativo pode não estar usando reflexão diretamente, mas uma montagem de terceiros que você está fazendo referência pode estar usando-o.

Quando o código está fazendo referência a uma API através da reflexão e você não quer que o linker corte o conjunto que contém essa API, você pode modificar seu arquivo de projeto para excluir o conjunto do processo de corte. O exemplo a seguir mostra `System.Security` como evitar que uma assembléia chamada seja aparada:

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="see-also"></a>Confira também

- [Implantação de aplicativos .NET Core](index.md)
