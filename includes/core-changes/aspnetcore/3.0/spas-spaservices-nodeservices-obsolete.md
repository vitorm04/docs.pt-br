---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394117"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a>SPAs: SpaServices e NodeServices marcados como obsoletos

O conteúdo dos seguintes pacotes NuGet tem sido desnecessário desde ASP.NET Core 2.1. Consequentemente, os seguintes pacotes estão sendo marcados como obsoletos:

- [Microsoft.AspNetCore.SpaServices](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [Microsoft.AspNetCore.NodeServices](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

Pela mesma razão, os seguintes módulos npm estão sendo marcados como preteridos:

- [aspnet-angular](https://www.npmjs.com/package/aspnet-angular)
- [aspnet-prerendering](https://www.npmjs.com/package/aspnet-prerendering)
- [aspnet-webpack](https://www.npmjs.com/package/aspnet-webpack)
- [aspnet-webpack-react](https://www.npmjs.com/package/aspnet-webpack-react)
- [domínio-tarefa](https://www.npmjs.com/package/domain-task)

Os pacotes anteriores e os módulos npm serão posteriormente removidos em .NET 5.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Os pacotes preteridos e os módulos npm foram destinados a integrar ASP.NET Core com várias estruturas de SPA (Single-Page App). Tais estruturas incluem Angular, React e React com Redux.

#### <a name="new-behavior"></a>Novo comportamento

Existe um novo mecanismo de integração no pacote [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet. O pacote continua sendo a base dos modelos de projeto Angular e React desde ASP.NET Core 2.1.

#### <a name="reason-for-change"></a>Motivo da mudança

ASP.NET Core suporta a integração com várias estruturas de Aplicativo de Página Única (SPA), incluindo Angular, React e React com Redux. Inicialmente, a integração com esses frameworks foi realizada com ASP.NET componentes específicos do Core que lidavam com cenários como pré-renderização do lado do servidor e integração com o Webpack. Com o passar do tempo, os padrões da indústria mudaram. Cada uma das estruturas de SPA lançou suas próprias interfaces padrão de linha de comando. Por exemplo, CLI angular e create-react-app.

Quando ASP.NET Core 2.1 foi lançado em maio de 2018, a equipe respondeu à mudança nos padrões. Uma maneira mais nova e simples de se integrar com as próprias cadeias de ferramentas das estruturas spa foi fornecida. O novo mecanismo de `Microsoft.AspNetCore.SpaServices.Extensions` integração existe no pacote e continua sendo a base dos modelos angular e react do projeto desde ASP.NET Core 2.1.

Para esclarecer que os componentes mais antigos ASP.NET específicos do Núcleo são irrelevantes e não recomendados:

- O mecanismo de integração pré-2.1 é marcado como obsoleto.
- Os pacotes npm de suporte são marcados como preteridos.

#### <a name="recommended-action"></a>Ação recomendada

Se você estiver usando esses pacotes, atualize seus aplicativos para usar a funcionalidade:

- No `Microsoft.AspNetCore.SpaServices.Extensions` pacote.
- Fornecido pelas estruturas de SPA que você está usando

Para habilitar recursos como pré-renderização do lado do servidor e recarga de módulo quente, consulte a documentação da estrutura spa correspondente. A funcionalidade `Microsoft.AspNetCore.SpaServices.Extensions` *não* é obsoleta e continuará a ser suportada.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.AspNetCore.Builder.SpaRouteExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.WebpackDevMiddleware?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.INodeServices?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesFactory?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesOptions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.StringAsTempFile?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions?displayProperty=nameWithType>

- <xref:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Builder.SpaRouteExtensions`
- `T:Microsoft.AspNetCore.Builder.WebpackDevMiddleware`

- `T:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader`
- `T:Microsoft.AspNetCore.NodeServices.INodeServices`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesFactory`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesOptions`
- `T:Microsoft.AspNetCore.NodeServices.StringAsTempFile`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance`

- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult`
- `T:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions`

- `T:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions`
- `T:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions`

-->
