---
ms.openlocfilehash: 78678b4b352bb063d1521e9aee3492c0cee059b8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720975"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="56918-101">InvalidAsynchronousStateException movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="56918-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="56918-102">A <xref:System.ComponentModel.InvalidAsynchronousStateException> classe foi movida.</span><span class="sxs-lookup"><span data-stu-id="56918-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="56918-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="56918-103">Change description</span></span>

<span data-ttu-id="56918-104">No .NET Core 2,2 e versões anteriores, a <xref:System.ComponentModel.InvalidAsynchronousStateException> classe é encontrada no assembly *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="56918-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="56918-105">A partir do .NET Core 3,0, ele é encontrado no assembly *System. ComponentModel. primitivas* .</span><span class="sxs-lookup"><span data-stu-id="56918-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="56918-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="56918-106">Version introduced</span></span>

<span data-ttu-id="56918-107">3.0</span><span class="sxs-lookup"><span data-stu-id="56918-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="56918-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="56918-108">Recommended action</span></span>

<span data-ttu-id="56918-109">Essa alteração afeta apenas os aplicativos que usam a reflexão para carregar o <xref:System.ComponentModel.InvalidAsynchronousStateException> chamando um método como <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ou uma sobrecarga de <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> que assume que o tipo está em um assembly específico.</span><span class="sxs-lookup"><span data-stu-id="56918-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="56918-110">Se esse for o caso, atualize o assembly referenciado na chamada de método para refletir o novo local do assembly do tipo.</span><span class="sxs-lookup"><span data-stu-id="56918-110">If that is the case, update the assembly referenced in the method call to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="56918-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="56918-111">Category</span></span>

<span data-ttu-id="56918-112">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="56918-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="56918-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="56918-113">Affected APIs</span></span>

<span data-ttu-id="56918-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="56918-114">None.</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis

-->
