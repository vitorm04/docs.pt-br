---
ms.openlocfilehash: a5b3e325c13d2f56532ebc6ebb5c259d565a4952
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235104"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="be2d4-101">XmlSchemaException agora define posições de linhas corretamente</span><span class="sxs-lookup"><span data-stu-id="be2d4-101">XmlSchemaException now sets line positions properly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="be2d4-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="be2d4-102">Details</span></span>|<span data-ttu-id="be2d4-103">Se o valor <xref:System.Xml.Linq.LoadOptions.SetLineInfo> é passado para o método Load e um erro de validação ocorre, as propriedades <xref:System.Xml.Schema.XmlSchemaException.LineNumber> e <xref:System.Xml.Schema.XmlSchemaException.LinePosition> contêm agora a linha de informações.</span><span class="sxs-lookup"><span data-stu-id="be2d4-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>|
|<span data-ttu-id="be2d4-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="be2d4-104">Suggestion</span></span>|<span data-ttu-id="be2d4-105">O código de tratamento de exceção que supõe que <xref:System.Xml.Schema.XmlSchemaException.LineNumber> e <xref:System.Xml.Schema.XmlSchemaException.LinePosition> não serão definidas deverá ser atualizado, uma vez que essas propriedades agora serão definidas corretamente quando SetLineInfo for usado durante o carregamento de XML.</span><span class="sxs-lookup"><span data-stu-id="be2d4-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>|
|<span data-ttu-id="be2d4-106">Escopo</span><span class="sxs-lookup"><span data-stu-id="be2d4-106">Scope</span></span>|<span data-ttu-id="be2d4-107">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="be2d4-107">Edge</span></span>|
|<span data-ttu-id="be2d4-108">Versão</span><span class="sxs-lookup"><span data-stu-id="be2d4-108">Version</span></span>|<span data-ttu-id="be2d4-109">4.5</span><span class="sxs-lookup"><span data-stu-id="be2d4-109">4.5</span></span>|
|<span data-ttu-id="be2d4-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="be2d4-110">Type</span></span>|<span data-ttu-id="be2d4-111">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="be2d4-111">Runtime</span></span>|
|<span data-ttu-id="be2d4-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="be2d4-112">Affected APIs</span></span>|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
