---
ms.openlocfilehash: 668d047d3247d64cb1400d4a9ea6887795fa0d44
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803149"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="9a6c0-101">A propriedade HttpRequest.ContentEncoding proíbe a UTF7</span><span class="sxs-lookup"><span data-stu-id="9a6c0-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9a6c0-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="9a6c0-102">Details</span></span>|<span data-ttu-id="9a6c0-103">A partir do .NET Framework 4.5, a codificação UTF-7 está proibida nos corpos de <xref:System.Web.HttpRequest?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="9a6c0-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=name>s' bodies.</span></span> <span data-ttu-id="9a6c0-104">Os dados para aplicativos que dependem de dados de entrada UTF-7 não serão decodificados corretamente em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="9a6c0-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>|
|<span data-ttu-id="9a6c0-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="9a6c0-105">Suggestion</span></span>|<span data-ttu-id="9a6c0-106">De modo ideal, os aplicativos devem ser atualizados para não usar a codificação UTF-7 em <xref:System.Web.HttpRequest?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="9a6c0-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=name>s.</span></span> <span data-ttu-id="9a6c0-107">De modo alternativo, o comportamento herdado pode ser restaurado usando o atributo <code>aspnet:AllowUtf7RequestContentEncoding</code> do elemento [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="9a6c0-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) element.</span></span>|
|<span data-ttu-id="9a6c0-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="9a6c0-108">Scope</span></span>|<span data-ttu-id="9a6c0-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="9a6c0-109">Edge</span></span>|
|<span data-ttu-id="9a6c0-110">Versão</span><span class="sxs-lookup"><span data-stu-id="9a6c0-110">Version</span></span>|<span data-ttu-id="9a6c0-111">4.5</span><span class="sxs-lookup"><span data-stu-id="9a6c0-111">4.5</span></span>|
|<span data-ttu-id="9a6c0-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="9a6c0-112">Type</span></span>|<span data-ttu-id="9a6c0-113">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="9a6c0-113">Runtime</span></span>|
|<span data-ttu-id="9a6c0-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="9a6c0-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
