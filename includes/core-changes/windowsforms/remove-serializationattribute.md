---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217041"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="1cc14-101">SerializableAttribute removido de alguns tipos de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1cc14-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="1cc14-102">O <xref:System.SerializableAttribute> foi removido de algumas classes de Windows Forms que não têm cenários de serialização binária conhecidos.</span><span class="sxs-lookup"><span data-stu-id="1cc14-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1cc14-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="1cc14-103">Change description</span></span>

<span data-ttu-id="1cc14-104">Os tipos a seguir são decorados com <xref:System.SerializableAttribute> o no .NET Framework, mas o atributo foi removido no .NET Core:</span><span class="sxs-lookup"><span data-stu-id="1cc14-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

<span data-ttu-id="1cc14-105">Historicamente, esse mecanismo de serialização teve preocupações sérias em manutenção e segurança.</span><span class="sxs-lookup"><span data-stu-id="1cc14-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="1cc14-106">Manter `SerializableAttribute` em tipos significa que esses tipos devem ser testados para alterações de serialização de versão para versão e alterações de serialização de estrutura para estrutura potencialmente.</span><span class="sxs-lookup"><span data-stu-id="1cc14-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="1cc14-107">Isso dificulta a evolução desses tipos e pode ser dispendioso para manter.</span><span class="sxs-lookup"><span data-stu-id="1cc14-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="1cc14-108">Esses tipos não têm nenhum cenário de serialização binária conhecido, o que minimiza o impacto da remoção do atributo.</span><span class="sxs-lookup"><span data-stu-id="1cc14-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="1cc14-109">Para obter mais informações, consulte [serialização binária](~/docs/standard/serialization/binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="1cc14-109">For more information, see [Binary serialization](~/docs/standard/serialization/binary-serialization.md).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1cc14-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="1cc14-110">Version introduced</span></span>

<span data-ttu-id="1cc14-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="1cc14-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1cc14-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="1cc14-112">Recommended action</span></span>

<span data-ttu-id="1cc14-113">Atualize qualquer código que possa depender desses tipos sendo marcados como serializáveis.</span><span class="sxs-lookup"><span data-stu-id="1cc14-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="1cc14-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="1cc14-114">Category</span></span>

<span data-ttu-id="1cc14-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1cc14-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1cc14-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1cc14-116">Affected APIs</span></span>

- <span data-ttu-id="1cc14-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="1cc14-117">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
