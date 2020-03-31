---
title: O que há de novo no .NET Standard
description: Este artigo resume os novos recursos e melhorias encontrados em cada nova versão do .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 28d6a3546e08bbc3a7d4a26f08ba9cc5e16a901b
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438199"
---
# <a name="whats-new-in-net-standard"></a>O que há de novo no .NET Standard

.NET Standard é uma especificação formal que define um conjunto de APIs com versões que devem estar disponíveis em implementações .NET que estejam em conformidade com essa versão da norma. .NET Standard é direcionado a desenvolvedores de bibliotecas. Uma biblioteca direcionada a uma versão do .NET Standard pode ser usada em qualquer implementação do .NET Framework, do .NET Core ou do Xamarin que dê suporte a essa versão do Standard.

O .NET Standard está incluído no .NET Core SDK, bem como no Visual Studio quando você seleciona a carga de trabalho .NET Core.

## <a name="supported-net-implementations"></a>Implementações .NET com suporte

.NET Standard 2.0 é suportado pelas seguintes implementações .NET:

- .NET Core 2.0 ou posterior
- .NET Framework 4.6.1 ou posterior
- Mono 5.4 ou posterior
- Xamarin.iOS 10.14 ou posterior
- Xamarin.Mac 3.8 ou posterior
- Xamarin.Android 8.0 ou posterior
- Plataforma Universal do Windows 10.0.16299 ou posterior

## <a name="whats-new-in-net-standard-20"></a>O que há de novo no .NET Standard 2.0

.NET Standard 2.0 inclui os seguintes novos recursos:

### <a name="a-vastly-expanded-set-of-apis"></a>Um conjunto muito maior de APIs

Através da versão 1.6, o .NET Standard incluiu um subconjunto relativamente pequeno de APIs. Entre os excluídos estavam várias APIs usadas normalmente no .NET Framework ou no Xamarin. Isso complica o desenvolvimento, pois exige que os desenvolvedores encontrem substituições adequadas para APIs conhecidas quando desenvolvem aplicativos e bibliotecas direcionadas a várias implementações do .NET. .NET Standard 2.0 aborda essa limitação adicionando mais 20.000 APIs a mais do que estavam disponíveis no .NET Standard 1.6, a versão anterior do padrão. Para obter uma lista das APIs adicionadas ao .NET Standard 2.0, consulte [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

Algumas das adições ao namespace <xref:System> no .NET Standard 2.0 incluem:

- Suporte para a classe <xref:System.AppDomain>.
- Aprimoramento do suporte para trabalhar com matrizes de membros adicionais na classe <xref:System.Array>.
- Aprimoramento do suporte para trabalhar com atributos de membros adicionais na classe <xref:System.Attribute>.
- Aprimoramento do suporte ao calendário e opções de formatação adicionais para valores <xref:System.DateTime>.
- Funcionalidade de arredondamento <xref:System.Decimal> adicional.
- Funcionalidade adicional na classe <xref:System.Environment>.
- Aprimoramento do controle sobre o coletor de lixo por meio da classe <xref:System.GC>.
- Aprimoramento do suporte para comparação, enumeração e normalização de cadeia de caracteres na classe <xref:System.String>.
- Suporte para ajustes de horário de verão e tempos de transição nas classes <xref:System.TimeZoneInfo.AdjustmentRule> e <xref:System.TimeZoneInfo.TransitionTime>.
- Aprimoramento considerável da funcionalidade na classe <xref:System.Type>.
- Aprimoramento do suporte para desserialização de objetos de exceção com a adição de um construtor de exceção com os parâmetros <xref:System.Runtime.Serialization.SerializationInfo> e <xref:System.Runtime.Serialization.StreamingContext>.

### <a name="support-for-net-framework-libraries"></a>Suporte a bibliotecas do .NET Framework

A esmagadora maioria das bibliotecas tem como alvo o .NET Framework em vez do .NET Standard. No entanto, a maioria das chamadas nessas bibliotecas são para APIs incluídas no .NET Standard 2.0. A partir do .NET Standard 2.0, você pode acessar bibliotecas .NET Framework a partir de uma biblioteca .NET Standard usando um [shim de compatibilidade](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification). Essa camada de compatibilidade é transparente para os desenvolvedores; você não precisa fazer nada para tirar proveito das bibliotecas do .NET Framework.

O único requisito é que as APIs chamadas pela biblioteca de classes .NET Framework devem ser incluídas no .NET Standard 2.0.

### <a name="support-for-visual-basic"></a>Suporte para Visual Basic

Agora, você pode desenvolver bibliotecas .NET Standard no Visual Basic. Visual Studio 2019 e Visual Studio 2017 versão 15.3 ou posterior com a carga de trabalho .NET Core instalada incluem um modelo .NET Standard Class Library. Para desenvolvedores em Visual Basic que usam outros ambientes e ferramentas de desenvolvimento, use o comando [dotnet new](../../core/tools/dotnet-new.md) para criar um projeto de biblioteca do .NET Standard. Para saber mais, confira o [Suporte a ferramentas para bibliotecas .NET Standard](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>Suporte a ferramentas para bibliotecas .NET Standard

Com o lançamento do .NET Core 2.0 e do .NET Standard 2.0, tanto o Visual Studio 2017 quanto o [.NET Core CLI](../../core/tools/index.md) incluem suporte de ferramentas para criar bibliotecas .NET Standard.

Se instalar o Visual Studio com a carga de trabalho **desenvolvimento de plataforma cruzada do .NET Core**, você poderá criar um projeto de biblioteca .NET Standard 2.0 usando um modelo de projeto, como mostra a figura a seguir:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

![Adicionar um novo projeto de biblioteca .NET Standard](./media/std-project-cs.png)

Se você estiver usando o .NET Core CLI, o novo comando [dotnet](../../core/tools/dotnet-new.md) a seguir criará um projeto de biblioteca de classes que tem como alvo o .NET Standard 2.0:

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

![Adicionar um novo projeto de biblioteca .NET Standard](./media/std-project-vb.png)

Se você estiver usando o .NET Core CLI, o novo comando [dotnet](../../core/tools/dotnet-new.md) a seguir criará um projeto de biblioteca de classes que tem como alvo o .NET Standard 2.0:

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Confira também

- [.NET Standard](../net-standard.md)
- [Apresentando o .NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
