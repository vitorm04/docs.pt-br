---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394401"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a>MVC: Shim de compatibilidade da API web removido

A partir de ASP.NET Core `Microsoft.AspNetCore.Mvc.WebApiCompatShim` 3.0, o pacote não está mais disponível.

#### <a name="change-description"></a>Descrição da alteração

O `Microsoft.AspNetCore.Mvc.WebApiCompatShim` pacote (WebApiCompatShim) fornece compatibilidade parcial no ASP.NET Core com ASP.NET API 2 da Web para simplificar as implementações de API da Web existentes migratórias para ASP.NET Core. No entanto, os aplicativos que usam o WebApiCompatShim não se beneficiam dos recursos relacionados à API enviados nos últimos lançamentos do ASP.NET Core. Esses recursos incluem uma melhor geração de especificação de API Aberta, manipulação padronizada de erros e geração de código do cliente. Para melhor concentrar os esforços da API no 3.0, o WebApiCompatShim foi removido. Os aplicativos existentes que usam o WebApiCompatShim devem migrar para o modelo mais `[ApiController]` novo.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="reason-for-change"></a>Motivo da mudança

O shim de compatibilidade da API da Web era uma ferramenta de migração. Ele restringe o acesso do usuário a novas funcionalidades adicionadas no ASP.NET Core.

#### <a name="recommended-action"></a>Ação recomendada

Remova o uso deste shim e migre diretamente para a funcionalidade semelhante no próprio ASP.NET Core.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
