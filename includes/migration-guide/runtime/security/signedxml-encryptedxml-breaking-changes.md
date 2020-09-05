---
ms.openlocfilehash: 5c8ea3565fbe599dd53a71ba8bd339704f7d7f8a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497337"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a><span data-ttu-id="30982-101">Alterações de falha de SignedXml e EncryptedXml</span><span class="sxs-lookup"><span data-stu-id="30982-101">SignedXml and EncryptedXml Breaking Changes</span></span>

#### <a name="details"></a><span data-ttu-id="30982-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="30982-102">Details</span></span>

<span data-ttu-id="30982-103">No .NET Framework 4.6.2, correções de segurança em <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> e <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> levam a comportamentos de tempo de execução diferentes.</span><span class="sxs-lookup"><span data-stu-id="30982-103">In .NET Framework 4.6.2, Security fixes in <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> and <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> lead to different run-time behaviors.</span></span> <span data-ttu-id="30982-104">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="30982-104">For example,</span></span><ul><li><span data-ttu-id="30982-105">Se um documento tiver vários elementos com o mesmo atributo <code>id</code> e uma assinatura tiver como destino um desses elementos como a raiz da assinatura, o documento agora será considerado inválido.</span><span class="sxs-lookup"><span data-stu-id="30982-105">If a document has multiple elements with the same <code>id</code> attribute and a signature targets one of those elements as the root of the signature, the document will now be considered invalid.</span></span></li><li><span data-ttu-id="30982-106">Documentos que usam algoritmos de transformação XPath não canônicos nas referências agora são considerados inválidos.</span><span class="sxs-lookup"><span data-stu-id="30982-106">Documents using non-canonical XPath transform algorithms in references are now considered invalid.</span></span></li><li><span data-ttu-id="30982-107">Documentos que usam algoritmos de transformação XSLT não canônicos nas referências agora são considerados inválidos.</span><span class="sxs-lookup"><span data-stu-id="30982-107">Documents using non-canonical XSLT transform algorithms in references are now consider invalid.</span></span></li><li><span data-ttu-id="30982-108">Nenhum programa que usar assinaturas desanexadas de recursos externos poderá fazer isso.</span><span class="sxs-lookup"><span data-stu-id="30982-108">Any program making use of external resource detached signatures will be unable to do so.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="30982-109">Sugestão</span><span class="sxs-lookup"><span data-stu-id="30982-109">Suggestion</span></span>

<span data-ttu-id="30982-110">Talvez os desenvolvedores queiram revisar o uso de <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> e <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, bem como dos tipos derivados de <xref:System.Security.Cryptography.Xml.Transform>, uma vez que o receptor de um documento poderá não conseguir processá-lo.</span><span class="sxs-lookup"><span data-stu-id="30982-110">Developers might want to review the usage of <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> and <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, as well as types derived from <xref:System.Security.Cryptography.Xml.Transform> since a document receiver may not be able to process it.</span></span>

| <span data-ttu-id="30982-111">Nome</span><span class="sxs-lookup"><span data-stu-id="30982-111">Name</span></span>    | <span data-ttu-id="30982-112">Valor</span><span class="sxs-lookup"><span data-stu-id="30982-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="30982-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="30982-113">Scope</span></span>   |<span data-ttu-id="30982-114">Secundária</span><span class="sxs-lookup"><span data-stu-id="30982-114">Minor</span></span>|
|<span data-ttu-id="30982-115">Versão</span><span class="sxs-lookup"><span data-stu-id="30982-115">Version</span></span>|<span data-ttu-id="30982-116">4.6.2</span><span class="sxs-lookup"><span data-stu-id="30982-116">4.6.2</span></span>|
|<span data-ttu-id="30982-117">Tipo</span><span class="sxs-lookup"><span data-stu-id="30982-117">Type</span></span>|<span data-ttu-id="30982-118">Runtime</span><span class="sxs-lookup"><span data-stu-id="30982-118">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="30982-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="30982-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.Xml.Transform`
- `T:System.Security.Cryptography.Xml.XmlDsigXPathTransform`
- `T:System.Security.Cryptography.Xml.XmlDsigXsltTransform`

-->
