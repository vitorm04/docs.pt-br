---
ms.openlocfilehash: c3e39e49747be709977d7fba3c39b59f5575c40d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619907"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="12f19-101">XmlSchemaException agora define posições de linhas corretamente</span><span class="sxs-lookup"><span data-stu-id="12f19-101">XmlSchemaException now sets line positions properly</span></span>

#### <a name="details"></a><span data-ttu-id="12f19-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="12f19-102">Details</span></span>

<span data-ttu-id="12f19-103">Se o valor <xref:System.Xml.Linq.LoadOptions.SetLineInfo> é passado para o método Load e um erro de validação ocorre, as propriedades <xref:System.Xml.Schema.XmlSchemaException.LineNumber> e <xref:System.Xml.Schema.XmlSchemaException.LinePosition> contêm agora a linha de informações.</span><span class="sxs-lookup"><span data-stu-id="12f19-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="12f19-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="12f19-104">Suggestion</span></span>

<span data-ttu-id="12f19-105">O código de tratamento de exceção que supõe que <xref:System.Xml.Schema.XmlSchemaException.LineNumber> e <xref:System.Xml.Schema.XmlSchemaException.LinePosition> não serão definidas deverá ser atualizado, uma vez que essas propriedades agora serão definidas corretamente quando SetLineInfo for usado durante o carregamento de XML.</span><span class="sxs-lookup"><span data-stu-id="12f19-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>

| <span data-ttu-id="12f19-106">Name</span><span class="sxs-lookup"><span data-stu-id="12f19-106">Name</span></span>    | <span data-ttu-id="12f19-107">Valor</span><span class="sxs-lookup"><span data-stu-id="12f19-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="12f19-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="12f19-108">Scope</span></span>   |<span data-ttu-id="12f19-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="12f19-109">Edge</span></span>|
|<span data-ttu-id="12f19-110">Versão</span><span class="sxs-lookup"><span data-stu-id="12f19-110">Version</span></span>|<span data-ttu-id="12f19-111">4.5</span><span class="sxs-lookup"><span data-stu-id="12f19-111">4.5</span></span>|
|<span data-ttu-id="12f19-112">Type</span><span class="sxs-lookup"><span data-stu-id="12f19-112">Type</span></span>|<span data-ttu-id="12f19-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="12f19-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="12f19-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="12f19-114">Affected APIs</span></span>

-<xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
