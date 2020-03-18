---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937276"
---
### <a name="target-framework-net-framework-support-dropped"></a>Quadro de destino: o suporte ao framework .NET caiu

Começando com ASP.NET Core 3.0, o .NET Framework é uma estrutura de destino não suportada.

#### <a name="change-description"></a>Descrição da alteração

.NET Framework 4.8 é a última versão principal do .NET Framework. Os novos aplicativos ASP.NET Core devem ser construídos no .NET Core. Começando com a versão .NET Core 3.0, você pode pensar em ASP.NET Core 3.0 como sendo parte do .NET Core.

Os clientes que usam ASP.NET Core com o .NET Framework podem continuar de forma totalmente suportada usando a [versão 2.1 LTS](https://www.microsoft.com/net/download/dotnet-core/2.1). O suporte e a manutenção do 2.1 continua até pelo menos 21 de agosto de 2021. Esta data é de três anos após a declaração da liberação do LTS pela [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy). O suporte para ASP.NET pacotes Core 2.1 **no .NET Framework** se estenderá indefinidamente, semelhante à [política de manutenção para outros frameworks de ASP.NET baseados em pacotes.](https://dotnet.microsoft.com/platform/support/policy/aspnet)

Para obter mais informações sobre a portação do .NET Framework para .NET Core, consulte [Porting to .NET Core](~/docs/core/porting/index.md).

`Microsoft.Extensions`pacotes (como registro, injeção de dependência e configuração) e Entity Framework Core não são afetados. Eles continuarão a apoiar o .NET Standard.

Para obter mais informações sobre a motivação dessa mudança, consulte [o post original do blog](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

ASP.NET os aplicativos Core podem ser executados no .NET Core ou no .NET Framework.

#### <a name="new-behavior"></a>Novo comportamento

ASP.NET aplicativos Core só podem ser executados no .NET Core.

#### <a name="recommended-action"></a>Ação recomendada

Execute uma das seguintes ações:

- Mantenha seu aplicativo no ASP.NET Core 2.1.
- Migre seu aplicativo e suas dependências para o .NET Core.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
