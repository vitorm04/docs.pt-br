---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041653"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a>Identidade: a interface do usuário usa o recurso de ativos da Web estáticos

O ASP.NET Core 3,0 introduziu um recurso de ativos da Web estático e a interface do usuário da identidade o adotou.

#### <a name="change-description"></a>Alterar descrição

Como resultado da interface do usuário de identidade adotando o recurso de ativos da Web estáticos:

- A seleção de estrutura é realizada usando a propriedade `IdentityUIFrameworkVersion` em seu arquivo de projeto.
- A inicialização 4 é a estrutura de interface do usuário padrão para a interface do usuário de identidade. A inicialização 3 atingiu o fim da vida útil e você deve considerar a migração para uma versão com suporte.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

A estrutura de interface do usuário padrão da interface do usuário de identidade foi a **inicialização 3**. A estrutura da interface do usuário pode ser configurada usando um parâmetro para a chamada do método `AddDefaultUI` em `Startup.ConfigureServices`.

#### <a name="new-behavior"></a>Novo comportamento

A estrutura de interface do usuário padrão para identidade de interface do usuário é **Bootstrap 4**. A estrutura da interface do usuário deve ser configurada em seu arquivo de projeto, em vez de na chamada do método `AddDefaultUI`.

#### <a name="reason-for-change"></a>Motivo da alteração

A adoção do recurso de ativos da Web estáticos exigia que a configuração da estrutura da interface do usuário se mova para o MSBuild. A decisão sobre qual estrutura deve ser inserida é uma decisão em tempo de compilação, não uma decisão de tempo de execução.

#### <a name="recommended-action"></a>Ação recomendada

Examine a interface do usuário do site para garantir que os novos componentes Bootstrap 4 sejam compatíveis. Se necessário, use a propriedade do MSBuild `IdentityUIFrameworkVersion` para reverter para a inicialização 3. Adicione a propriedade a um elemento `<PropertyGroup>` em seu arquivo de projeto:

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
