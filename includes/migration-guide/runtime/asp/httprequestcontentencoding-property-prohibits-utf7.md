---
ms.openlocfilehash: 668d047d3247d64cb1400d4a9ea6887795fa0d44
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235032"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="6ac71-101">A propriedade HttpRequest.ContentEncoding proíbe a UTF7</span><span class="sxs-lookup"><span data-stu-id="6ac71-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6ac71-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="6ac71-102">Details</span></span>|<span data-ttu-id="6ac71-103">A partir do .NET Framework 4.5, a codificação UTF-7 está proibida nos corpos de <xref:System.Web.HttpRequest?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="6ac71-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=name>s' bodies.</span></span> <span data-ttu-id="6ac71-104">Os dados para aplicativos que dependem de dados de entrada UTF-7 não serão decodificados corretamente em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="6ac71-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>|
|<span data-ttu-id="6ac71-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="6ac71-105">Suggestion</span></span>|<span data-ttu-id="6ac71-106">De modo ideal, os aplicativos devem ser atualizados para não usar a codificação UTF-7 em <xref:System.Web.HttpRequest?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="6ac71-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=name>s.</span></span> <span data-ttu-id="6ac71-107">De modo alternativo, o comportamento herdado pode ser restaurado usando o atributo <code>aspnet:AllowUtf7RequestContentEncoding</code> do elemento [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="6ac71-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) element.</span></span>|
|<span data-ttu-id="6ac71-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="6ac71-108">Scope</span></span>|<span data-ttu-id="6ac71-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="6ac71-109">Edge</span></span>|
|<span data-ttu-id="6ac71-110">Versão</span><span class="sxs-lookup"><span data-stu-id="6ac71-110">Version</span></span>|<span data-ttu-id="6ac71-111">4.5</span><span class="sxs-lookup"><span data-stu-id="6ac71-111">4.5</span></span>|
|<span data-ttu-id="6ac71-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="6ac71-112">Type</span></span>|<span data-ttu-id="6ac71-113">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="6ac71-113">Runtime</span></span>|
|<span data-ttu-id="6ac71-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6ac71-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
