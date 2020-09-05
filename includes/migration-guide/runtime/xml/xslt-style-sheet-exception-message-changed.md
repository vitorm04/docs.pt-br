---
ms.openlocfilehash: d33d75b4c2d9bc18844f66f1fcca1e2efc6f1eee
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496393"
---
### <a name="xslt-style-sheet-exception-message-changed"></a><span data-ttu-id="53fc1-101">Mensagem de exceção da folha de estilos XSLT alterada</span><span class="sxs-lookup"><span data-stu-id="53fc1-101">XSLT style sheet exception message changed</span></span>

#### <a name="details"></a><span data-ttu-id="53fc1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="53fc1-102">Details</span></span>

<span data-ttu-id="53fc1-103">No .NET Framework 4,5, o texto da mensagem de erro quando um arquivo XSLT é muito complexo é &quot; a folha de estilos muito complexa. &quot; Em versões anteriores, a mensagem de erro era &quot; erro de compilação de XSLT. &quot; O código do aplicativo que depende do texto da mensagem de erro não funcionará mais.</span><span class="sxs-lookup"><span data-stu-id="53fc1-103">In the .NET Framework 4.5, the text of the error message when an XSLT file is too complex is &quot;The style sheet is too complex.&quot; In previous versions, the error message was &quot;XSLT compile error.&quot; Application code that depends on the text of the error message will no longer work.</span></span> <span data-ttu-id="53fc1-104">No entanto, os tipos de exceção permanecem os mesmos, de modo que essa modificação não deve ter um impacto real.</span><span class="sxs-lookup"><span data-stu-id="53fc1-104">However, the exception types remain the same, so this change should have no real impact.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="53fc1-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="53fc1-105">Suggestion</span></span>

<span data-ttu-id="53fc1-106">Atualize qualquer código de aplicativo, dependendo da mensagem de exceção dessa condição de erro, para esperar a nova mensagem ou (ainda melhor) atualize o código para depender somente do tipo de exceção (<xref:System.Xml.Xsl.XsltException?displayProperty=fullName>), que não foi alterado.</span><span class="sxs-lookup"><span data-stu-id="53fc1-106">Update any app code depending on the exception message from this error condition to expect the new message, or (even better) update the code to depend only on the exception type (<xref:System.Xml.Xsl.XsltException?displayProperty=fullName>), which has not changed.</span></span>

| <span data-ttu-id="53fc1-107">Nome</span><span class="sxs-lookup"><span data-stu-id="53fc1-107">Name</span></span>    | <span data-ttu-id="53fc1-108">Valor</span><span class="sxs-lookup"><span data-stu-id="53fc1-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="53fc1-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="53fc1-109">Scope</span></span>   |<span data-ttu-id="53fc1-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="53fc1-110">Edge</span></span>|
|<span data-ttu-id="53fc1-111">Versão</span><span class="sxs-lookup"><span data-stu-id="53fc1-111">Version</span></span>|<span data-ttu-id="53fc1-112">4.5</span><span class="sxs-lookup"><span data-stu-id="53fc1-112">4.5</span></span>|
|<span data-ttu-id="53fc1-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="53fc1-113">Type</span></span>|<span data-ttu-id="53fc1-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="53fc1-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="53fc1-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="53fc1-115">Affected APIs</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.String)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)`

-->
