---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394127"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Kestrel: Conjunto HTTPS vazio removido

A <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> assembléia foi removida.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="reason-for-change"></a>Motivo da mudança

Em ASP.NET Núcleo 2.1, `Microsoft.AspNetCore.Server.Kestrel.Https` o <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>conteúdo foi transferido para . Essa mudança foi feita de forma `[TypeForwardedTo]` não-quebra usando atributos.

#### <a name="recommended-action"></a>Ação recomendada

- Bibliotecas referentes `Microsoft.AspNetCore.Server.Kestrel.Https` ao 2.0 devem atualizar todas as dependências ASP.NET Core para 2.1 ou posterior. Caso contrário, eles podem quebrar quando carregados em um aplicativo ASP.NET Core 3.0.
- Aplicativos e bibliotecas direcionados ao ASP.NET Core 2.1 e `Microsoft.AspNetCore.Server.Kestrel.Https` posteriores devem remover quaisquer referências diretas ao pacote NuGet.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
