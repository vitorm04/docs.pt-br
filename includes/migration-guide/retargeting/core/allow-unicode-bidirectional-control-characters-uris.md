---
ms.openlocfilehash: 53d74db1a77e62cc64250658281fd3e4706fe494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614269"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a><span data-ttu-id="ded06-101">Permitir caracteres de controle bidirecionais Unicode em URIs</span><span class="sxs-lookup"><span data-stu-id="ded06-101">Allow Unicode Bidirectional Control Characters in URIs</span></span>

#### <a name="details"></a><span data-ttu-id="ded06-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ded06-102">Details</span></span>

<span data-ttu-id="ded06-103">O Unicode especifica vários caracteres de controle especiais usados para especificar a orientação do texto.</span><span class="sxs-lookup"><span data-stu-id="ded06-103">Unicode specifies several special control characters used to specify the orientation of text.</span></span> <span data-ttu-id="ded06-104">Nas versões anteriores do .NET Framework, esses caracteres eram excluídos incorretamente de todos os URIs mesmo quando estavam presentes em sua forma codificada por porcentagem.</span><span class="sxs-lookup"><span data-stu-id="ded06-104">In previous versions of the .NET Framework, these characters were incorrectly stripped from all URIs even if they were present in their percent-encoded form.</span></span> <span data-ttu-id="ded06-105">Para atender melhor ao [RFC 3987](https://tools.ietf.org/html/rfc3987), agora esses caracteres são permitidos nos URIs.</span><span class="sxs-lookup"><span data-stu-id="ded06-105">In order to better follow [RFC 3987](https://tools.ietf.org/html/rfc3987), we now allow these characters in URIs.</span></span> <span data-ttu-id="ded06-106">Quando encontrados sem codificação em um URI, eles são codificados por porcentagem.</span><span class="sxs-lookup"><span data-stu-id="ded06-106">When found unencoded in a URI, they are percent-encoded.</span></span> <span data-ttu-id="ded06-107">Quando encontrados codificados por porcentagem, eles são deixados no estado em que se encontram.</span><span class="sxs-lookup"><span data-stu-id="ded06-107">When found percent-encoded they are left as-is.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ded06-108">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ded06-108">Suggestion</span></span>

<span data-ttu-id="ded06-109">Para aplicativos direcionados a versões do .NET Framework começando com a 4.7.2, o suporte para caracteres bidirecionais Unicode é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="ded06-109">For applications that target versions of .NET Framework starting with 4.7.2, support for Unicode bidirectional characters is enabled by default.</span></span> <span data-ttu-id="ded06-110">Se essa alteração não for desejada, você poderá desabilitá-la adicionando a seguinte opção [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) à seção `<runtime>` do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ded06-110">If this change is undesirable, you can disable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true" />
</runtime>
```

<span data-ttu-id="ded06-111">Para aplicativos direcionados a versões anteriores do .NET Framework, mas executados em versões começando com o .NET Framework 4.7.2, o suporte para caracteres bidirecionais Unicode é desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="ded06-111">For applications that target earlier versions of the .NET Framework but are running under versions starting with .NET Framework 4.7.2, support for Unicode bidirectional characters is disabled by default.</span></span> <span data-ttu-id="ded06-112">Você poderá habilitá-la adicionando a seguinte opção [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) à seção `<runtime>` do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ded06-112">You can enable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file::</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false" />
</runtime>
```

| <span data-ttu-id="ded06-113">Name</span><span class="sxs-lookup"><span data-stu-id="ded06-113">Name</span></span>    | <span data-ttu-id="ded06-114">Valor</span><span class="sxs-lookup"><span data-stu-id="ded06-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ded06-115">Escopo</span><span class="sxs-lookup"><span data-stu-id="ded06-115">Scope</span></span>   | <span data-ttu-id="ded06-116">Secundária</span><span class="sxs-lookup"><span data-stu-id="ded06-116">Minor</span></span>       |
| <span data-ttu-id="ded06-117">Versão</span><span class="sxs-lookup"><span data-stu-id="ded06-117">Version</span></span> | <span data-ttu-id="ded06-118">4.7.2</span><span class="sxs-lookup"><span data-stu-id="ded06-118">4.7.2</span></span>       |
| <span data-ttu-id="ded06-119">Type</span><span class="sxs-lookup"><span data-stu-id="ded06-119">Type</span></span>    | <span data-ttu-id="ded06-120">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="ded06-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ded06-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ded06-121">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
