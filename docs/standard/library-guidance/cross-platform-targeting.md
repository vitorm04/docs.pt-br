---
title: Direcionamento de plataforma cruzada
description: Práticas recomendadas para a criação de bibliotecas do .NET de plataforma cruzada.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 72fa891d5b1054af485a98d89b4efb11d6b0018b
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374878"
---
# <a name="cross-platform-targeting"></a>Direcionamento de plataforma cruzada

.NET modernos dá suporte a vários sistemas operacionais e dispositivos. É importante para as bibliotecas de código-fonte aberto do .NET dar suporte a desenvolvedores tantos quanto possível, se eles estão criando um site ASP.NET hospedado no Azure ou um jogo de .NET no Unity.

## <a name="net-standard"></a>.NET Standard

.NET standard é a melhor maneira de adicionar suporte de plataforma cruzada em uma biblioteca do .NET. [.NET standard](../net-standard.md) é uma especificação de APIs .NET que estão disponíveis em todas as implementações do .NET. Direcionamento para .NET Standard permite produzir bibliotecas que são restritos a usar as APIs que estão em uma determinada versão do .NET Standard, que significa que ele é usado por todas as plataformas que implementam essa versão do .NET Standard.

![.NET standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")

Direcionamento para .NET Standard e compilar com êxito o projeto, não garantem que a biblioteca será executado com êxito em todas as plataformas:

1. APIs específicas da plataforma falhará em outras plataformas. Por exemplo, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> será bem-sucedida no Windows e lançar <xref:System.PlatformNotSupportedException> quando usado em qualquer outro sistema operacional.
2. APIs podem se comportar de maneira diferente. Por exemplo, reflexão APIs têm diferentes características de desempenho quando um aplicativo usa a compilação ahead of time em iOS ou UWP.

> [!TIP]
> A equipe do .NET [oferece um analisador Roslyn](../analyzers/api-analyzer.md) para ajudá-lo a descobrir possíveis problemas.

**FAZER ✔️** começar com incluindo um `netstandard2.0` destino.

> Mais bibliotecas de uso geral não devem precisar de APIs fora do .NET Standard 2.0. .NET standard 2.0 é compatível com todas as plataformas modernas e é a maneira recomendada para dar suporte a várias plataformas com um destino.

**❌ Evite** incluindo um `netstandard1.x` destino.

> .NET standard 1.x é distribuído como um conjunto granular de pacotes do NuGet, que cria um gráfico de dependência de pacote grande e resulta em download de muitos pacotes durante a criação de desenvolvedores. Plataformas .NET modernas, incluindo o .NET Framework 4.6.1, UWP e Xamarin, o suporte .NET Standard 2.0. Você deve somente direcionar o .NET Standard 1.x se você precisar especificamente para ter como destino uma plataforma mais antiga.

**FAZER ✔️** incluem uma `netstandard2.0` de destino se você precisar de um `netstandard1.x` destino.

> Todas as plataformas que dão suporte a .NET Standard 2.0 usará o `netstandard2.0` de destino e se beneficiar de um grafo de pacote menor enquanto plataformas mais antigas ainda funcionarão e voltar a usar o `netstandard1.x` destino.

**❌ NÃO** incluir um destino .NET Standard, se a biblioteca se baseia em um modelo de aplicativo específico da plataforma.

> Por exemplo, uma biblioteca do Kit de ferramentas de controle UWP depende de um modelo de aplicativo que está disponível apenas em UWP. Específico ao modelo de aplicativo APIs não estará disponíveis no .NET Standard.

## <a name="multi-targeting"></a>Multiplataforma

Às vezes, você precisará acessar APIs específicas da estrutura de suas bibliotecas. A melhor maneira de chamar APIs específicas da estrutura é usando o multi-direcionamento, que compila seu projeto para muitos [estruturas de destino do .NET](../frameworks.md) em vez de apenas um.

Para proteger seus consumidores de ter que criar para estruturas individuais, você deve se esforçar para ter uma saída de .NET Standard além de uma ou mais saídas específicas da estrutura. Com o multi-direcionamento, todos os assemblies são empacotados dentro de um único pacote NuGet. Os consumidores podem fazer referência o mesmo pacote e NuGet escolherá a implementação apropriada. Sua biblioteca .NET Standard serve como a biblioteca de fallback é usado em todos os lugares, exceto para os casos em que o seu pacote do NuGet oferece uma implementação específica do framework. Multiplataforma permite que você usar a compilação condicional em seu código e chamar APIs específicas da estrutura.

![Pacote NuGet com vários assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "pacote NuGet com vários assemblies")

**Considere a possibilidade de ✔️** direcionamento implementações do .NET, além do .NET Standard.

> Direcionamento de implementações do .NET permite que você chame APIs específicas da plataforma que estão fora do .NET Standard.
>
> Não remova o suporte para o .NET Standard ao fazer isso. Em vez disso, lançar da implementação e oferecem APIs de recurso. Dessa forma, sua biblioteca pode ser usada em qualquer lugar e dá suporte ao tempo de execução light-up dos recursos.

**❌ Evite** usando multiplataforma com o .NET Standard se seu código-fonte é o mesmo para todos os destinos.

> O assembly .NET padrão será usado automaticamente pelo NuGet. Direcionamento de implementações de .NET individuais aumenta a `*.nupkg` tamanho sem nenhum benefício.

**Considere a possibilidade de ✔️** adicionando um destino para `net461` quando você está oferecendo uma `netstandard2.0` destino. 

> Usar o .NET Standard 2.0 do .NET Framework tem alguns problemas que foram resolvidos no .NET Framework 4.7.2. Você pode melhorar a experiência para desenvolvedores que ainda estão no .NET Framework 4.6.1 - 4.7.1, oferecendo a eles um binário que é compilado para .NET Framework 4.6.1.

**FAZER ✔️** distribuir sua biblioteca usando um pacote do NuGet.

> NuGet selecionará o melhor destino para o desenvolvedor e protegê-las ter que ler a implementação apropriada.

**FAZER ✔️** usar um arquivo de projeto `TargetFrameworks` propriedade quando vários destinos.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

**Considere a possibilidade de ✔️** usando [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) quando multi-targeting para UWP e Xamarin, que simplifica muito o seu arquivo de projeto.

## <a name="older-targets"></a>Destinos mais antigos

.NET dá suporte a versões de direcionamento do .NET Framework longos sem suporte, bem como em plataformas não são mais comumente usadas. Embora não haja valor fazer seu trabalho de biblioteca em como muitos destinos quanto possível, necessidade de trabalhar em torno de APIs ausentes podem adicionar significativa sobrecarga. Acreditamos que determinadas estruturas não são mais que vale a pena direcionamento, considerando seu alcance e limitações.

**❌ NÃO** incluir um destino de biblioteca de classe portátil (PCL). Por exemplo, `portable-net45+win8+wpa81+wp8`.

> .NET standard é a maneira moderna para dar suporte a bibliotecas do .NET de plataforma cruzada e substitui PCLs.

**❌ NÃO** incluir destinos para plataformas do .NET que não têm mais suporte. Por exemplo, `SL4`, `WP`.

>[!div class="step-by-step"]
[Anterior](./get-started.md)
[Próximo](./strong-naming.md)
