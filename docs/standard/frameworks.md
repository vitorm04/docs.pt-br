---
title: Estruturas de destino | Microsoft Docs
description: "As informações sobre estruturas de destino para os aplicativos e bibliotecas do .NET Core."
keywords: .NET, .NET Core, estrutura, TFM
author: richlander
ms.author: mairaw
ms.date: 04/27/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6ef56a2e-593d-497b-925a-1e25bb6df2e6
ms.translationtype: Machine Translation
ms.sourcegitcommit: 45835eb80642253f80ea630ae9db1ac766b72b9c
ms.openlocfilehash: 11c1f11e4f8354b7573d03e680cf4a8a16fa26d9
ms.contentlocale: pt-br
ms.lasthandoff: 05/11/2017

---

# <a name="target-frameworks"></a>Frameworks de destino

*Estruturas* definem os objetos, métodos e ferramentas que você usa para criar aplicativos e bibliotecas. O .NET Framework é usado para criar aplicativos e bibliotecas principalmente para execução em sistemas que executam um sistema operacional Windows. O .NET core inclui uma estrutura que permite a compilação de aplicativos e bibliotecas executados em diversos sistemas operacionais.

Às vezes, os termos de *estrutura* e *plataforma* são confusos de acordo com a forma como são usados em frases. Piorando ainda mais a interpretação, o termo *plataforma* tem significados diferentes em contextos diferentes. Por exemplo, você verá ".NET Core" descrito como "estrutura do .NET Core" no contexto da compilação de aplicativos e bibliotecas e também descrito como "plataforma .NET Core" no contexto em que o código da biblioteca e do aplicativo é executado. A *plataforma de computação* descreve *onde e como* um aplicativo é executado. Como o .NET Core executa código com o [.NET Core Common Language Runtime (CoreCLR)](https://github.com/dotnet/coreclr), ele também é uma plataforma. O mesmo vale para o .NET Framework, que tem o [Common Language Runtime (CLR)](clr.md) para executar o código do aplicativo e da biblioteca que foi desenvolvido com os objetos de estrutura, métodos e ferramentas do .NET Framework. Você verá com frequência o termo "multiplataforma" na documentação; mas quando você vir esse termo, pense "múltiplos sistemas operacionais e múltiplas arquiteturas (x86, x64, arm)", pois esse é o significado que o autor geralmente pretende transmitir.

Os objetos e métodos das estruturas são chamados de APIs (Interfaces de programação de aplicativo). As APIs de Estrutura são usadas no [Visual Studio](https://www.visualstudio.com/), [Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac/), [Visual Studio Code](https://code.visualstudio.com/) e outros IDEs (Ambientes de desenvolvimento integrados) e editores para fornecer o conjunto correto de objetos e métodos para desenvolvimento. As estruturas também são usadas pelo [NuGet](https://www.nuget.org/) para produção e consumo de pacotes do NuGet, para garantir que você produza e use pacotes apropriados para as estruturas direcionadas em seu aplicativo ou biblioteca.

Quando você *direciona uma estrutura* ou várias delas, decida quais conjuntos de APIs e quais versões dessas APIs você deseja usar. As estruturas são referenciadas de várias maneiras: por nome de produto, nomes de estrutura longos ou curtos e por família.

## <a name="referring-to-frameworks"></a>Referindo-se a estruturas

Há várias maneiras para fazer referência a estruturas, a maioria delas é usada em toda a documentação do .NET Core. Usando o .NET Framework 4.6.2 como exemplo, os formatos a seguir podem ser usados:

**Referindo-se a um produto**

Você pode se referir a um tempo de execução ou plataforma .NET. Ambos são igualmente válidos.

* .NET Framework 4.6.2
* .NET 4.6.2

**Referindo-se a uma estrutura**

Você pode se referir a uma estrutura ou ao direcionamento de uma estrutura usando formas longas ou curtas do TFM. Ambos são igualmente válidos.

* `.NETFramework,Version=4.6.2`
* `net462`

**Referindo-se a uma família de estruturas**

Você pode se referir a uma família estruturas usando formas longas ou curtas da ID da estrutura. Ambos são igualmente válidos.

* `.NETFramework`
* `net`

## <a name="latest-framework-versions"></a>Versões mais recentes da estrutura

A tabela a seguir define o conjunto de estruturas que podem ser usadas, como elas são chamadas e qual versão do [.NET Standard Library](library.md) elas implementam. Estas versões do Framework são as versões estáveis mais recentes. As versões de pré-lançamento não são mostradas.

| Framework             | Última Versão | TFM (Moniker de Estrutura de Destino) | TFM (Moniker de Estrutura de Destino) Compacto | Versão do .NET Standard | Metapacote |
| :-------------------: | :------------: | :----------------------------: | :------------------------------------: | :-------------------: | :---------: |
| .NET Standard         | 1.6.1          | .NETStandard,Version=1.6       | netstandard1.6                         | N/D                   | [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) |
| .NET Core Application | 1.1.1          | .NETCoreApp,Version=1.1        | netcoreapp1.1                          | 1.6                   | [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) |
| .NET Framework        | 4.6.2          | .NETFramework,Version=4.6.2    | net462                                 | 1.5                   | N/A |

## <a name="supported-frameworks"></a>Estruturas com suporte

Normalmente, uma estrutura é referenciada por um moniker curto de estrutura de destino ou *TFM*. No .NET Standard, isso também é generalizado para *TxM* a fim de permitir uma única referência para várias estruturas. Os clientes do NuGet oferecem suporte às seguintes estruturas. Equivalentes são mostrados entre colchetes (`[]`).

| Nome                       | Abreviação de | TFMs/TxMs                                    |
| -------------------------- | ------------ | -------------------------------------------- |
| .NET Standard              | netstandard  | netstandard1.0                               |
|                            |              | netstandard1.1                               |
|                            |              | netstandard1.2                               |
|                            |              | netstandard1.3                               |
|                            |              | netstandard1.4                               |
|                            |              | netstandard1.5                               |
|                            |              | netstandard1.6                               |
| .NET Core                  | netcoreapp   | netcoreapp1.0                                |
|                            |              | netcoreapp1.1                                |
| .NET Framework             | net          | net11                                        |
|                            |              | net20                                        |
|                            |              | net35                                        |
|                            |              | net40                                        |
|                            |              | net403                                       |
|                            |              | net45                                        |
|                            |              | net451                                       |
|                            |              | net452                                       |
|                            |              | net46                                        |
|                            |              | net461                                       |
|                            |              | net462                                       |
| Windows Store              | netcore      | netcore [netcore45]                          |
|                            |              | netcore45 [win, win8]                        |
|                            |              | netcore451 [win81]                           |
| .NET Micro Framework       | netmf        | netmf                                        |
| Silverlight                | sl           | sl4                                          |
|                            |              | sl5                                          |
| Windows Phone              | wp           | wp [wp7]                                     |
|                            |              | wp7                                          |
|                            |              | wp75                                         |
|                            |              | wp8                                          |
|                            |              | wp81                                         |
|                            |              | wpa81                                        |
| Plataforma Universal do Windows | uap          | uap [uap10.0]                                |
|                            |              | uap10.0 [win10] [netcore50]                  |

## <a name="deprecated-frameworks"></a>Estruturas preteridas

As seguintes estruturas são preteridas. Os pacotes direcionados a essas estruturas devem ser migrados para as substituições indicadas.

| Estrutura preterida | Substituição |
| -------------------- | ----------- |
| aspnet50             | netcoreapp  |
| aspnetcore50         |             |
| dnxcore50            |             |
| dnx                  |             |
| dnx45                |             |
| dnx451               |             |
| dnx452               |             |
| dotnet               | netstandard |
| dotnet50             |             |
| dotnet51             |             |
| dotnet52             |             |
| dotnet53             |             |
| dotnet54             |             |
| dotnet55             |             |
| dotnet56             |             |
| netcore50            | uap10.0     |
| win                  | netcore45   |
| win8                 | netcore45   |
| win81                | netcore451  |
| win10                | uap10.0     |
| winrt                | netcore45   |

## <a name="precedence"></a>Precedência

Várias estruturas relacionadas e compatíveis entre si, mas não necessariamente equivalentes:

| Framework                        | Pode usar   |
| -------------------------------- | --------- |
| uap (Plataforma Universal do Windows) | win81     |
|                                  | wpa81     |
|                                  | netcore50 |
| win (Windows Store)              | winrt     |
|                                  | winrt45   |

## <a name="net-standard"></a>.NET Standard

O [.NET Standard](https://github.com/dotnet/standard) simplifica referências entre estruturas compatíveis com o binário, permitindo que uma estrutura de destino única faça referência a uma combinação de outras. Para saber mais, veja o tópico [.NET Standard Library](library.md).

[Ferramentas NuGet Obter a ferramenta de estrutura mais próxima](http://nugettoolsdev.azurewebsites.net/) simula a lógica do NuGet usada para a seleção de uma estrutura de muitos ativos de estrutura disponíveis em um pacote com base na estrutura do projeto. Para usar a ferramenta, entra em uma estrutura de projeto e um ou mais estruturas de pacote. Selecione o botão **Enviar**. A ferramenta indica se as estruturas de pacote listadas são compatíveis com a estrutura de projeto que você fornecer.

## <a name="portable-class-libraries"></a>Bibliotecas de Classes Portáteis

Para obter informações sobre as Bibliotecas de Classe Portáteis, veja a seção [Bibliotecas de Classes Portáteis](https://docs.microsoft.com/nuget/schema/target-frameworks#portable-class-libraries) do tópico *Estrutura de Destino* na documentação do NuGet. Stephen Cleary criou uma ferramenta que lista as PCLs com suporte. Para saber mais, confira [Perfis de estrutura no .NET](http://blog.stephencleary.com/2012/05/framework-profiles-in-net.html).

