---
title: "Controle de versão do .NET Core | Microsoft Docs"
description: "Controle de Versão do .NET Core"
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: f6f684b1-1d2c-4105-8376-7c1959e23803
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 3cdd3ff040bfd9d307f0d0c0a07fbd0d972cbd3e
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---

# <a name="net-core-versioning"></a>Controle de Versão do .NET Core

O .NET Core é uma plataforma dos [pacotes NuGet](../packages.md), estruturas e distribuído como uma unidade. Cada uma dessas camadas de plataforma pode ter controle de versão para agilidade de produto e para descrever com precisão as alterações do produto. Embora haja uma flexibilidade significativa de controle de versão, há um desejo de controlar a versão da plataforma como uma unidade para facilitar a compreensão do produto.

O produto é único em alguns aspectos, sendo descritos e entregue por meio de um gerenciador de pacotes (NuGet) como pacotes. Embora o .NET Core geralmente seja adquirido como um SDK autônomo, o SDK é muito mais conveniente do que pacotes NuGet e, portanto não são diferentes de pacotes. Como resultado, o controle de versão ocorre principalmente com relação aos pacotes e outras experiências de controle de versão a partir daqui.

## <a name="semantic-versioning"></a>Controle de Versão Semântico

O .NET Core [SemVer (Controle de Versão Semântico)](http://semver.org/), adotando o uso de controle de versão principal.secundária.patch, usando as diversas partes do número de versão para descrever o grau e tipo de alteração.

O modelo de controle de versão a seguir geralmente é aplicado ao .NET Core. Há casos em que ele foi adaptado para caber no controle de versão existente. Tais casos serão descritos posteriormente neste documento. Por exemplo, estruturas só devem representar recursos de plataforma e de API, que estão alinhados com o controle de versão principal/secundária.

### <a name="versioning-form"></a>Formato do Controle de Versão

PRINCIPAL.SECUNDÁRIA.PATCH[-PRÉLANÇAMENTO-NÚMERODAVERSÃO]

### <a name="decision-tree"></a>Árvore de Decisão

PRINCIPAL quando:
  - remover o suporte de uma plataforma
  - adotar uma versão PRINCIPAL mais recente de uma dependência existente 
  - desabilitar uma sutileza de compatibilidade por padrão

SECUNDÁRIA quando:
  - adicionar área de superfície de API pública 
  - adicionar novo comportamento
  - adotar uma versão SECUNDÁRIA mais recente de uma dependência existente
  - introduzir uma nova dependência 
  
PATCH quando:
  - corrigir bugs
  - adicionar suporte a uma plataforma mais recente
  - adotar uma versão PATCH mais recente de uma dependência existente
  - qualquer outra alteração (não captada por outros pontos)

Ao determinar o que deve ser incrementado quando há várias alterações, escolha o tipo mais alto de alteração.

## <a name="versioning-scheme"></a>Esquema de Controle de Versão

O .NET Core pode ser definido e sua versão controlada da seguinte maneira:

- Uma implementação de tempo de execução e estrutura distribuídos como pacotes. Cada pacote tem controle de versão independente, especialmente para controle de versão de patch.
- Um conjunto de metapacotes que fazem referência a pacotes refinados como uma unidade com controle de versão. Metapacotes têm controle de versão separado dos pacotes.
- Um conjunto de estruturas (por exemplo, `netstandard`) que representa um conjunto de APIs cada vez maior, descrito em um conjunto de instantâneos com controle de versão.

### <a name="packages"></a>Pacotes

Pacotes de biblioteca evoluem e mudam de versão independentemente. Pacotes que coincidem com o .NET Framework System.\* assemblies normalmente usam versões 4. x, alinhadas com o controle de versão do .NET Framework 4. x (uma opção histórica). Pacotes que não coincidem com as bibliotecas do .NET Framework (por exemplo, [System.Reflection.Metadata](https://www.nuget.org/packages/System.Reflection.Metadata)) normalmente começam em 1.0 e aumentam a partir daí.

Os pacotes descritos por [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) são tratados de forma especial por estarem na base da plataforma.

- Pacotes de NETStandard.Library normalmente têm controle de versão como um conjunto, visto que eles têm dependências de nível de implementação entre eles.
- As APIs só serão adicionadas aos pacotes NETStandard.Library como parte das versões principais ou secundárias do .NET Core, visto que fazer isso exigiria adicionar uma nova versão `netstandard`. Isso é uma adição aos requisitos de SemVer.

### <a name="metapackages"></a>Metapacotes

O controle de versão para metapacotes .NET Core baseia-se na estrutura à qual eles são mapeados. Os metapacotes adotam o maior número de versão de estrutura (por exemplo, netstandard1.6) ao qual eles são mapeados no fechamento do pacote. 

A versão de patch para o metapacote é usada para representar as atualizações para o metapacote fazer referência a pacotes atualizados. Versões de patch nunca incluirão uma versão de estrutura atualizada. Como resultado, os metapacotes não são estritamente compatíveis com SemVer, pois seu esquema de controle de versão não representa o nível de alteração nos pacotes subjacentes, mas principalmente no nível de API. 

Há dois metapacotes principais para o .NET Core.

**NETStandard.Library**

- v1.6 a partir do .NET Core 1.0 (essas versões normalmente e intencionalmente não coincidem).
- É mapeado para a estrutura `netstandard`. 
- Descreve os pacotes que são considerados necessários para o desenvolvimento de aplicativos modernos e que plataformas .NET devem implementar para serem consideradas uma plataforma [.NET Standard](../../standard/library.md).

**Microsoft.NETCore.App**

- v1.0 a partir do .NET Core 1.0 (essas versões coincidem).
- É mapeado para a estrutura `netcoreapp`.
- Descreve os pacotes na distribuição do .NET Core.

Observação: [`Microsoft.NETCore.Portable.Compatibility`](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) é outro metapacote do .NET Core. Ele não é mapeado para uma determinada estrutura, por isso as versões funcionam como um pacote.

### <a name="frameworks"></a>Estruturas

As versões de estruturas são atualizadas quando novas APIs são adicionadas. Elas não têm conceito de versão de patch, visto que representam a forma da API e não as questões de implementação. O controle de versão principal e secundária seguirá as regras de SemVer especificadas anteriormente.

A estrutura `netcoreapp` está vinculada à distribuição .NET Core. Ele seguirá os números de versão usados pelo .NET Core. Por exemplo, quando o .NET Core 2.0 for lançado, ele será direcionada para o `netcoreapp2.0`. A estrutura `netstandard` não coincidirá com o esquema de controle de versão de qualquer tempo de execução do .NET, visto que é igualmente aplicável a todos eles.

## <a name="versioning-in-practice"></a>Controle de Versão na Prática

Há confirmações e PRs em repositórios do .NET Core no GitHub diariamente, resultando em novas compilações de muitas bibliotecas. Não é viável criar novas versões públicas do .NET Core para cada alteração. Em vez disso, as alterações serão agregadas por um período vagamente definido (por exemplo, semanas ou meses) antes de criar uma nova versão estável pública do .NET Core.

Uma nova versão do .NET Core pode significar várias coisas:

- Novas versões de pacotes e metapacotes.
- Novas versões das várias estruturas, considerando a adição de novas APIs.
- Nova versão da distribuição do .NET Core.

### <a name="shipping-a-patch-release"></a>Enviando uma versão de patch

Após o envio de uma versão estável do .NET Core v1.0.0, alterações no nível de patch (não há novas APIs) são feitas em bibliotecas .NET Core para corrigir bugs e melhorar o desempenho e a confiabilidade. Os vários metapacotes são atualizados para referenciar os pacotes de biblioteca atualizados do .NET Core. Os metapacotes têm controle de versão como atualizações de patch (x.y.z). As estruturas não são atualizadas. Uma nova distribuição .NET Core é lançada com um número de versão correspondente ao metapacote `Microsoft.NETCore.App`.

Você pode ver as atualizações de patch demonstradas nos exemplos de project.json abaixo.

```
{
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.1"
  },
  "frameworks": {
    "netcoreapp1.0": {}
  }
}
```

### <a name="shipping-a-minor-release"></a>Enviando uma versão secundária

Após o envio de uma versão estável do .NET Core v1.0.0, novas APIs são adicionadas às bibliotecas .NET Core para habilitar novos cenários. Os vários metapacotes são atualizados para referenciar os pacotes de biblioteca atualizados do .NET Core. Os metapacotes têm controle de versão como atualizações de patch (x.y) para coincidir com a maior versão da estrutura. As diversas estruturas são atualizadas para descrever as novas APIs. Uma nova distribuição .NET Core é lançada com um número de versão correspondente ao metapacote `Microsoft.NETCore.App`.

Você pode ver atualizações secundárias demonstradas no seguinte arquivo de projeto:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp1.1</TargetFramework>
  </PropertyGroup>
</Project>
```

### <a name="shipping-a-major-release"></a>Enviando uma versão principal

Considerando uma versão estável .NET Core v1.y.z, novas APIs são adicionadas às bibliotecas do .NET Core para habilitar novos cenários principais. O suporte a uma plataforma pode ser removido. Os vários metapacotes são atualizados para referenciar os pacotes de biblioteca atualizados do .NET Core. O metapacote `Microsoft.NETCore.App` e a estrutura `netcore` têm controle de versão como uma atualização principal (x.). O metapacote `NETStandard.Library` normalmente tem controle de versão como uma atualização secundária (x.y), porque ele aplica-se a várias implementações do .NET. Uma nova distribuição do .NET Core é lançada com um número de versão correspondente ao metapacote `Microsoft.NETCore.App`.

Você pode ver as principais atualizações demonstradas no seguinte arquivo de projeto. (Observe que `netcoreapp2.0` não foi lançado.)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
  </PropertyGroup>
</Project>
```

