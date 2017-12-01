---
title: "O que há de novo no .NET Standard"
ms.custom: updateeachrelease
ms.date: 11/08/2017
ms.prod: .net
ms.topic: article
ms.technology: dotnet-standard
ms.##devlang: dotnet
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e938c009b79af3b2f36094bbb74f4d38baeeac0b
ms.sourcegitcommit: 281070dee88db86ec3bb4634d5f558d1a4e159dd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2017
---
# <a name="whats-new-in-the-net-standard"></a>O que há de novo no .NET Standard

O padrão do .NET é uma especificação formal que define um conjunto com controle de versão de APIs que devem estar disponíveis em implementações de .NET que estão em conformidade com essa versão do padrão. O .NET Standard é destinado a desenvolvedores de bibliotecas. Uma biblioteca que tem como alvo uma versão padrão do .NET pode ser usada em qualquer implementação do .NET Framework, o .NET Core ou Xamarin que dá suporte a essa versão do padrão.

A versão mais recente do padrão do .NET é 2.0. Ele está incluído com o SDK do .NET Core 2.0, bem como com o Visual Studio 2017 versão 15,3 com a carga de trabalho do .NET Core instalada.

## <a name="supported-net-implementations"></a>Implementações de .NET com suporte

O padrão de .NET 2.0 tem suporte as implementações de .NET a seguir:

- Núcleo do .NET 2.0
- .NET Framework 4.6.1
- Mono 5.4
- Xamarin 10.14
- Xamarin.Mac 3.8
- Xamarin 8.0
- Plataforma universal do Windows 10.0.16299

## <a name="whats-new-in-the-net-standard-20"></a>O que é novo no .NET 2.0 padrão
 
O padrão de .NET 2.0 inclui os seguintes novos recursos:

**Um conjunto muito maior de APIs**

A versão 1.6, padrão do .NET incluído um comparativamente pequeno subconjunto de APIs. Entre os excluídos foram várias APIs que foram usados no .NET Framework ou Xamarin. Isso complica a desenvolvimento, pois ele exige que os desenvolvedores localizar substituições adequadas para APIs familiar quando eles desenvolverem aplicativos e bibliotecas direcionadas a várias implementações de .NET. O padrão de .NET 2.0 endereços essa limitação, adicionando mais de 20.000 APIs mais que estavam disponíveis no .NET padrão 1.6, a versão anterior do padrão. Para obter uma lista das APIs que foram adicionadas ao .NET Standard 2.0, consulte [.NET 2.0 padrão vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md). 

Algumas das adições para o <xref:System> namespace .NET 2.0 padrão incluem:

- Suporte para o <xref:System.AppDomain> classe.
- Melhor suporte para trabalhar com matrizes de membros adicionais no <xref:System.Array> classe.
- Melhor suporte para trabalhar com os atributos dos membros adicionais no <xref:System.Attribute> classe.
- Calendário melhor suporte e as opções de formatação adicionais para <xref:System.DateTime> valores.
- Adicionais <xref:System.Decimal> funcionalidade de arredondamento.
- Funcionalidade adicional a <xref:System.Environment> classe.
- Aprimorado o controle sobre o coletor de lixo por meio de <xref:System.GC> classe.
- Suporte aprimorado para comparação de cadeia de caracteres, enumeração e normalização no <xref:System.String> classe.
- Suporte para horário de verão ajustes e tempos de transição no <xref:System.TimeZoneInfo.AdjustmentRule> e <xref:System.TimeZoneInfo.TransitionTime> classes.
- Aprimorada significativamente a funcionalidade de <xref:System.Type> classe.
- Melhor suporte para desserialização de objetos de exceção com a adição de um construtor de exceção com <xref:System.Runtime.Serialization.SerializationInfo> e <xref:System.Runtime.Serialization.StreamingContext> parâmetros.

**Suporte para bibliotecas do .NET Framework**

A grande maioria das bibliotecas de direcionar o .NET Framework em vez do .NET padrão. No entanto, a maioria das chamadas dessas bibliotecas é APIs que estão incluídos no .NET 2.0 padrão. Começando com o padrão de .NET 2.0, você pode acessar bibliotecas do .NET Framework em uma biblioteca .NET padrão usando um [correção de compatibilidade](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification). Essa camada de compatibilidade é transparente para os desenvolvedores; Você não precisa fazer nada para tirar proveito das bibliotecas do .NET Framework.

O único requisito é que as APIs chamadas por biblioteca de classes .NET Framework deve ser incluídas no .NET 2.0 padrão.

**Suporte para o Visual Basic**

Agora você pode desenvolver bibliotecas .NET padrão no Visual Basic. Para desenvolvedores do Visual Basic usando o Visual Studio 2017 versão 15,3 ou posterior com a carga de trabalho do .NET Core instalado, o Visual Studio agora inclui um modelo de biblioteca de classes .NET padrão. Para desenvolvedores do Visual Basic que usam outros ambientes e ferramentas de desenvolvimento, você pode usar o [dotnet novo](../../core/tools/dotnet-new.md) comando para criar um projeto de biblioteca padrão do .NET. Para obter mais informações, consulte o [suporte de ferramentas para as bibliotecas .NET padrão](#tooling).

<a name="tooling" />**Suporte de ferramentas para as bibliotecas .NET padrão**

Com o lançamento do núcleo do .NET 2.0 e o .NET 2.0 padrão, ambas as Visual Studio de 2017 e [.NET Core Interface de linha de comando (CLI)](../../core/tools/index.md) incluem o suporte de ferramentas para criar bibliotecas .NET padrão. 

Se você instalar o Visual Studio com o **desenvolvimento de plataforma cruzada do .NET Core** carga de trabalho, você pode criar um projeto de biblioteca do .NET 2.0 padrão usando um modelo de projeto, como mostra a figura a seguir. 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Adicionar projeto de biblioteca novo padrão do .NET](./media/std-project-cs.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
<a name="add-new-net-standard-library-projectmediastd-project-vbpng"></a>![Adicionar projeto de biblioteca novo padrão do .NET](./media/std-project-vb.png)
---

Se você estiver usando a CLI do .NET Core, o seguinte [dotnet novo](../../core/tools/dotnet-new.md) comando cria um projeto de biblioteca de classe que tem como alvo o .NET 2.0 padrão.

```csharp
dotnet new classlib
```
```vb
dotnet new classlib -lang vb
```
  
## <a name="see-also"></a>Consulte também
[Padrão do .NET](../net-standard.md)
[Introdução ao .NET padrão](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
