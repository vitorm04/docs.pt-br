---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449383"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="0c5ed-101">Não autorizadoAccessException lançado por FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="0c5ed-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="0c5ed-102">No .NET Core, um <xref:System.UnauthorizedAccessException> é jogado quando o chamador tenta definir um valor de atributo de arquivo, mas não tem permissão de gravação.</span><span class="sxs-lookup"><span data-stu-id="0c5ed-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0c5ed-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="0c5ed-103">Change description</span></span>

<span data-ttu-id="0c5ed-104">No .NET Framework, um <xref:System.ArgumentException> é jogado quando o chamador tenta definir um valor de atributo de arquivo, <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> mas não tem permissão de gravação.</span><span class="sxs-lookup"><span data-stu-id="0c5ed-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="0c5ed-105">Em .NET Core, um <xref:System.UnauthorizedAccessException> é jogado em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="0c5ed-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="0c5ed-106">(Em .NET Core, um <xref:System.ArgumentException> ainda é jogado se o chamador tentar definir um atributo de arquivo inválido.)</span><span class="sxs-lookup"><span data-stu-id="0c5ed-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0c5ed-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="0c5ed-107">Version introduced</span></span>

<span data-ttu-id="0c5ed-108">1.0</span><span class="sxs-lookup"><span data-stu-id="0c5ed-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0c5ed-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="0c5ed-109">Recommended action</span></span>

<span data-ttu-id="0c5ed-110">Modifique `catch` quaisquer instruções para pegar um <xref:System.UnauthorizedAccessException> em <xref:System.ArgumentException>vez de, ou, além de, um , conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="0c5ed-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="0c5ed-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="0c5ed-111">Category</span></span>

<span data-ttu-id="0c5ed-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="0c5ed-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0c5ed-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0c5ed-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
