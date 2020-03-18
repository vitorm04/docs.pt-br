---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73041653"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a>Identidade: A ui usa o recurso de ativos web estáticos

ASP.NET Core 3.0 introduziu um recurso de ativos web estáticos, e a II de identidade o adotou.

#### <a name="change-description"></a>Descrição da alteração

Como resultado da iu de identidade adotando o recurso de ativos web estáticos:

- A seleção do `IdentityUIFrameworkVersion` framework é realizada usando a propriedade em seu arquivo de projeto.
- Bootstrap 4 é a estrutura de interface do iu padrão para interface do iu de identidade. Bootstrap 3 chegou ao fim da vida útil, e você deve considerar migrar para uma versão suportada.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

A estrutura de interface do ui padrão para iu de identidade era **Bootstrap 3**. A estrutura de IA pode ser configurada usando um parâmetro para a chamada do `AddDefaultUI` método `Startup.ConfigureServices`.

#### <a name="new-behavior"></a>Novo comportamento

A estrutura de interface do rei padrão para interface do iu de identidade é **Bootstrap 4**. A estrutura de IA deve ser configurada no `AddDefaultUI` arquivo do projeto, em vez de na chamada do método.

#### <a name="reason-for-change"></a>Motivo da mudança

A adoção do recurso de ativos web estáticos exigiu que a configuração da estrutura de ida e qualquer outra seja para o MSBuild. A decisão sobre qual quadro incorporar é uma decisão de tempo de construção, não uma decisão em tempo de execução.

#### <a name="recommended-action"></a>Ação recomendada

Revise a interface do site para garantir que os novos componentes bootstrap 4 sejam compatíveis. Se necessário, `IdentityUIFrameworkVersion` use a propriedade MSBuild para reverter para Bootstrap 3. Adicione a propriedade `<PropertyGroup>` a um elemento no arquivo do projeto:

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
