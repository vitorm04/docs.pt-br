---
ms.openlocfilehash: 584014572ab799e1e3ab2f02c9fbf4fe6b0c17e7
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804914"
---
### <a name="blazor-updated-browser-support"></a>Mais incrivelmente: suporte a navegador atualizado

ASP.NET Core 5,0 apresenta [novos recursos mais avançados](https://github.com/dotnet/aspnetcore/issues/21514), alguns dos quais são incompatíveis com navegadores mais antigos. A lista de navegadores com suporte no mais 5,0 do ASP.NET Core foi atualizada de acordo.

Para obter uma discussão, consulte o problema do GitHub [dotnet/aspnetcore # 26475](https://github.com/dotnet/aspnetcore/issues/26475).

#### <a name="version-introduced"></a>Versão introduzida

5,0

#### <a name="old-behavior"></a>Comportamento antigo

O servidor mais incrivelmente dá suporte ao Microsoft Internet Explorer 11 com suportes retroativos suficientes. O servidor e Webassembly mais poseriais também são funcionais no [Microsoft Edge herdado](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).

#### <a name="new-behavior"></a>Novo comportamento

Não há suporte para um servidor mais incrivelmente no ASP.NET Core 5,0 com o Microsoft Internet Explorer 11. O servidor e o Webassembly mais completo não são totalmente funcionais no Microsoft Edge herdado.

#### <a name="reason-for-change"></a>Motivo da alteração

Novos recursos mais avançados do ASP.NET Core 5,0 são incompatíveis com esses navegadores mais antigos, e o uso desses navegadores mais antigos está diminuindo. Para saber mais, consulte os recursos a seguir:

* [O suporte do Windows para o Microsoft Edge herdado também está terminando em 9 de março de 2021](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)
* [Microsoft 365 aplicativos e serviços encerrarão o suporte para o Microsoft Internet Explorer 11 de 17 de agosto de 2021](/lifecycle/announcements/m365-ie11-microsoft-edge-legacy)

#### <a name="recommended-action"></a>Ação recomendada

Atualize esses navegadores mais antigos para o [novo Microsoft Edge baseado em Chromium](https://www.microsoft.com/edge). Para aplicativos mais incrivelmente que precisam dar suporte a esses navegadores mais antigos, use ASP.NET Core 3,1. A lista de navegadores com suporte para um mais incrivelmente no ASP.NET Core 3,1 não foi alterada e está documentada em [plataformas com suporte](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!--

#### Affected APIs

Not detectable via API analysis

-->
