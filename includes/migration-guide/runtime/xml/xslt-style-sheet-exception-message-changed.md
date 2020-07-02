---
ms.openlocfilehash: 5c27e8acdf30533036546ba4cca9e06877bde362
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619912"
---
### <a name="xslt-style-sheet-exception-message-changed"></a><span data-ttu-id="7364d-101">Mensagem de exceção da folha de estilos XSLT alterada</span><span class="sxs-lookup"><span data-stu-id="7364d-101">XSLT style sheet exception message changed</span></span>

#### <a name="details"></a><span data-ttu-id="7364d-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7364d-102">Details</span></span>

<span data-ttu-id="7364d-103">No .NET Framework 4,5, o texto da mensagem de erro quando um arquivo XSLT é muito complexo é &quot; a folha de estilos muito complexa. &quot; Em versões anteriores, a mensagem de erro era &quot; erro de compilação de XSLT. &quot; O código do aplicativo que depende do texto da mensagem de erro não funcionará mais.</span><span class="sxs-lookup"><span data-stu-id="7364d-103">In the .NET Framework 4.5, the text of the error message when an XSLT file is too complex is &quot;The style sheet is too complex.&quot; In previous versions, the error message was &quot;XSLT compile error.&quot; Application code that depends on the text of the error message will no longer work.</span></span> <span data-ttu-id="7364d-104">No entanto, os tipos de exceção permanecem os mesmos, de modo que essa modificação não deve ter um impacto real.</span><span class="sxs-lookup"><span data-stu-id="7364d-104">However, the exception types remain the same, so this change should have no real impact.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7364d-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="7364d-105">Suggestion</span></span>

<span data-ttu-id="7364d-106">Atualize qualquer código de aplicativo, dependendo da mensagem de exceção dessa condição de erro, para esperar a nova mensagem ou (ainda melhor) atualize o código para depender somente do tipo de exceção (<xref:System.Xml.Xsl.XsltException?displayProperty=fullName>), que não foi alterado.</span><span class="sxs-lookup"><span data-stu-id="7364d-106">Update any app code depending on the exception message from this error condition to expect the new message, or (even better) update the code to depend only on the exception type (<xref:System.Xml.Xsl.XsltException?displayProperty=fullName>), which has not changed.</span></span>

| <span data-ttu-id="7364d-107">Name</span><span class="sxs-lookup"><span data-stu-id="7364d-107">Name</span></span>    | <span data-ttu-id="7364d-108">Valor</span><span class="sxs-lookup"><span data-stu-id="7364d-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7364d-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="7364d-109">Scope</span></span>   |<span data-ttu-id="7364d-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="7364d-110">Edge</span></span>|
|<span data-ttu-id="7364d-111">Versão</span><span class="sxs-lookup"><span data-stu-id="7364d-111">Version</span></span>|<span data-ttu-id="7364d-112">4.5</span><span class="sxs-lookup"><span data-stu-id="7364d-112">4.5</span></span>|
|<span data-ttu-id="7364d-113">Type</span><span class="sxs-lookup"><span data-stu-id="7364d-113">Type</span></span>|<span data-ttu-id="7364d-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="7364d-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7364d-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="7364d-115">Affected APIs</span></span>

-<xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li></ul>|
