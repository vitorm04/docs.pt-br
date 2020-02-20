---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449383"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="1219e-101">UnauthorizedAccessException gerado por FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="1219e-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="1219e-102">No .NET Core, um <xref:System.UnauthorizedAccessException> é gerado quando o chamador tenta definir um valor de atributo de arquivo, mas não tem permissão de gravação.</span><span class="sxs-lookup"><span data-stu-id="1219e-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1219e-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="1219e-103">Change description</span></span>

<span data-ttu-id="1219e-104">No .NET Framework, um <xref:System.ArgumentException> é gerado quando o chamador tenta definir um valor de atributo de arquivo em <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>, mas não tem permissão de gravação.</span><span class="sxs-lookup"><span data-stu-id="1219e-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="1219e-105">No .NET Core, um <xref:System.UnauthorizedAccessException> é lançado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="1219e-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="1219e-106">(No .NET Core, um <xref:System.ArgumentException> ainda será gerado se o chamador tentar definir um atributo de arquivo inválido.)</span><span class="sxs-lookup"><span data-stu-id="1219e-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1219e-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="1219e-107">Version introduced</span></span>

<span data-ttu-id="1219e-108">1.0</span><span class="sxs-lookup"><span data-stu-id="1219e-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1219e-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="1219e-109">Recommended action</span></span>

<span data-ttu-id="1219e-110">Modifique quaisquer `catch` instruções para capturar um <xref:System.UnauthorizedAccessException> em vez de, ou além de, um <xref:System.ArgumentException>, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="1219e-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="1219e-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="1219e-111">Category</span></span>

<span data-ttu-id="1219e-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="1219e-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1219e-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1219e-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
