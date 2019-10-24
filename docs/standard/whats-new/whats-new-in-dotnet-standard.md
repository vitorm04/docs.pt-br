---
title: Novidades no .NET Standard
description: Este artigo resume os novos recursos e melhorias encontrados em cada nova versão do .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f69dfe77e5d485c4c7ffcbf2b98657eab87d452d
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775228"
---
# <a name="whats-new-in-the-net-standard"></a>Novidades no .NET Standard

O .NET Standard é uma especificação formal que define um conjunto com versões das APIs que devem estar disponíveis em implementações .NET que estejam de acordo com a versão standard. O .NET Standard é destinado a desenvolvedores de bibliotecas. Uma biblioteca direcionada a uma versão do .NET Standard pode ser usada em qualquer implementação do .NET Framework, do .NET Core ou do Xamarin que dê suporte a essa versão do Standard.

A versão mais recente do .NET Standard é a 2.0. Ele está incluído no SDK do .NET Core 2,0, bem como no Visual Studio 2017 versão 15,3 com a carga de trabalho do .NET Core instalada.

## <a name="supported-net-implementations"></a>Implementações .NET com suporte

O .NET Standard 2.0 tem suporte das seguintes implementações do .NET:

- .NET Core 2.0 ou posterior
- .NET Framework 4.6.1 ou posterior
- Mono 5.4 ou posterior
- Xamarin.iOS 10.14 ou posterior
- Xamarin.Mac 3.8 ou posterior
- Xamarin.Android 8.0 ou posterior
- Plataforma Universal do Windows 10.0.16299 ou posterior

## <a name="whats-new-in-the-net-standard-20"></a>Novidades no .NET Standard 2.0

O .NET Standard 2.0 inclui estes recursos novos:

### <a name="a-vastly-expanded-set-of-apis"></a>Um conjunto muito maior de APIs

Na versão 1.6, o .NET Standard incluía um subconjunto de APIs comparativamente pequeno. Entre os excluídos estavam várias APIs usadas normalmente no .NET Framework ou no Xamarin. Isso complica o desenvolvimento, pois exige que os desenvolvedores encontrem substituições adequadas para APIs conhecidas quando desenvolvem aplicativos e bibliotecas direcionadas a várias implementações do .NET. O .NET Standard 2.0 resolve essa limitação adicionando mais de 20.000 APIs que estavam disponíveis no .NET Standard 1.6, a versão anterior do Standard. Para obter uma lista com as APIs que foram adicionadas ao .NET Standard 2.0, confira [.NET Standard 2.0 versus 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

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

A grande maioria das bibliotecas são direcionadas ao .NET Framework em vez do .NET Standard. No entanto, a maioria das chamadas nessas bibliotecas são para APIs incluídas no .NET Standard 2.0. A partir do .NET Standard 2.0, você pode acessar bibliotecas do .NET Framework de uma biblioteca do .NET Standard usando uma [shim de compatibilidade](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification). Essa camada de compatibilidade é transparente para os desenvolvedores; você não precisa fazer nada para tirar proveito das bibliotecas do .NET Framework.

O único requisito é que as APIs chamadas pela biblioteca de classes .NET Framework estejam incluídas no .NET Standard 2.0.

### <a name="support-for-visual-basic"></a>Suporte para Visual Basic

Agora, você pode desenvolver bibliotecas .NET Standard no Visual Basic. Para Visual Basic desenvolvedores que usam o Visual Studio 2017 versão 15,3 ou posterior com a carga de trabalho do .NET Core instalada, o Visual Studio agora inclui um modelo de biblioteca de classes .NET Standard. Para desenvolvedores em Visual Basic que usam outros ambientes e ferramentas de desenvolvimento, use o comando [dotnet new](../../core/tools/dotnet-new.md) para criar um projeto de biblioteca do .NET Standard. Para saber mais, confira o [Suporte a ferramentas para bibliotecas .NET Standard](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>Suporte a ferramentas para bibliotecas .NET Standard

Com o lançamento do .NET Core 2.0 e do .NET Standard 2.0, o Visual Studio 2017 e a [CLI (Interface de linha de comando) do .NET Core](../../core/tools/index.md) incluem o suporte a ferramentas para criação de bibliotecas .NET Standard.

Se instalar o Visual Studio com a carga de trabalho **desenvolvimento de plataforma cruzada do .NET Core**, você poderá criar um projeto de biblioteca .NET Standard 2.0 usando um modelo de projeto, como mostra a figura a seguir:

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

![Adicionar um novo projeto de biblioteca .NET Standard](./media/std-project-cs.png)

Se você estiver usando a CLI do .NET Core, o seguinte comando [dotnet new](../../core/tools/dotnet-new.md) criará um projeto de biblioteca de classes direcionado ao .NET Standard 2.0:

```dotnetcli
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

![Adicionar um novo projeto de biblioteca .NET Standard](./media/std-project-vb.png)

Se você estiver usando a CLI do .NET Core, o seguinte comando [dotnet new](../../core/tools/dotnet-new.md) criará um projeto de biblioteca de classes direcionado ao .NET Standard 2.0:

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Consulte também

- [.NET Standard](../net-standard.md)
- [Apresentando o .NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
