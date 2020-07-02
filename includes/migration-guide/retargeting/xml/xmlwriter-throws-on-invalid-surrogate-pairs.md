---
ms.openlocfilehash: f87b70708398226516ab5eac32c24a9fc2c1106b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615601"
---
### <a name="xmlwriter-throws-on-invalid-surrogate-pairs"></a><span data-ttu-id="f47b6-101">XmlWriter é gerado com pares alternativos inválidos</span><span class="sxs-lookup"><span data-stu-id="f47b6-101">XmlWriter throws on invalid surrogate pairs</span></span>

#### <a name="details"></a><span data-ttu-id="f47b6-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f47b6-102">Details</span></span>

<span data-ttu-id="f47b6-103">Em aplicativos direcionados ao NET Framework 4.5.2 ou versões anteriores, escrever um par alternativo inválido usando o tratamento de fallback de exceção nem sempre gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="f47b6-103">For apps that target the .NET Framework 4.5.2 or previous versions, writing an invalid surrogate pair using exception fallback handling does not always throw an exception.</span></span> <span data-ttu-id="f47b6-104">Em aplicativos destinados ao .NET Framework 4.6, tentar escrever um par alternativo inválido gera <xref:System.ArgumentException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="f47b6-104">For apps that target the .NET Framework 4.6, attempting to write an invalid surrogate pair throws an <xref:System.ArgumentException?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f47b6-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="f47b6-105">Suggestion</span></span>

<span data-ttu-id="f47b6-106">Se necessário, essa interrupção pode ser evitada destinando ao .NET Framework 4.5.2 ou versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="f47b6-106">If necessary, this break can be avoided by targeting the .NET Framework 4.5.2 or earlier.</span></span> <span data-ttu-id="f47b6-107">Como alternativa, os pares alternativos inválidos podem ser pré-processados em um xml válido antes serem escritos.</span><span class="sxs-lookup"><span data-stu-id="f47b6-107">Alternatively, invalid surrogate pairs can be pre-processed into valid xml prior to writing them.</span></span>

| <span data-ttu-id="f47b6-108">Name</span><span class="sxs-lookup"><span data-stu-id="f47b6-108">Name</span></span>    | <span data-ttu-id="f47b6-109">Valor</span><span class="sxs-lookup"><span data-stu-id="f47b6-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f47b6-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="f47b6-110">Scope</span></span>   | <span data-ttu-id="f47b6-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f47b6-111">Edge</span></span>        |
| <span data-ttu-id="f47b6-112">Versão</span><span class="sxs-lookup"><span data-stu-id="f47b6-112">Version</span></span> | <span data-ttu-id="f47b6-113">4.6</span><span class="sxs-lookup"><span data-stu-id="f47b6-113">4.6</span></span>         |
| <span data-ttu-id="f47b6-114">Type</span><span class="sxs-lookup"><span data-stu-id="f47b6-114">Type</span></span>    | <span data-ttu-id="f47b6-115">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="f47b6-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="f47b6-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="f47b6-116">Affected APIs</span></span>

- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeStringAsync(System.String,System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCData(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCDataAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteChars(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCharsAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteComment(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCommentAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteEntityRef(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteEntityRefAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRaw(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteProcessingInstruction(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteProcessingInstructionAsync(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRaw(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRawAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRawAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteString(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteStringAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteSurrogateCharEntity(System.Char,System.Char)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteSurrogateCharEntityAsync(System.Char,System.Char)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteValue(System.String)?displayProperty=nameWithType>
