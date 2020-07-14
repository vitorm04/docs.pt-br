---
ms.openlocfilehash: b1d4b69b7a8ed68cd688dfd0249d5107b80e67c4
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281325"
---
### <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a>Localização: Construtor obsoleto removido no middleware de localização de solicitação

O <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> Construtor que não tem um <xref:Microsoft.Extensions.Logging.ILoggerFactory> parâmetro foi marcado como obsoleto [nesta confirmação](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0). No ASP.NET Core 5,0, o Construtor obsoleto foi removido. Para obter uma discussão, consulte [dotnet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785).

#### <a name="version-introduced"></a>Versão introduzida

5.0

#### <a name="old-behavior"></a>Comportamento antigo

O `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` Construtor obsoleto existe.

#### <a name="new-behavior"></a>Novo comportamento

O `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` Construtor obsoleto não existe.

#### <a name="reason-for-change"></a>Motivo da alteração

Essa alteração garante que o middleware de localização de solicitação sempre tenha acesso a um agente de log.

#### <a name="recommended-action"></a>Ação recomendada

Ao construir manualmente uma instância do `RequestLocalizationMiddleware` , passe uma `ILoggerFactory` instância no construtor. Se uma `ILoggerFactory` instância válida não estiver disponível nesse contexto, considere passar o construtor de middleware uma <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instância.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

[RequestLocalizationMiddleware. ctor (RequestDelegate, IOptions \<RequestLocalizationOptions> )](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
