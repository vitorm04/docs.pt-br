---
ms.openlocfilehash: c980b0c0be9f4d6a529baa0743dec9ac16ca0d7f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721639"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="c16b8-101">Não há suporte para a opção de compatibilidade UseLegacyImages</span><span class="sxs-lookup"><span data-stu-id="c16b8-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="c16b8-102">A `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade, que foi introduzida no .NET Framework 4,8, não tem suporte no Windows Forms no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="c16b8-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c16b8-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="c16b8-103">Change description</span></span>

<span data-ttu-id="c16b8-104">A partir do .NET Framework 4,8, a `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade resolveu possíveis problemas de dimensionamento de imagem em cenários de ClickOnce em ambientes de DPI alto.</span><span class="sxs-lookup"><span data-stu-id="c16b8-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="c16b8-105">Quando definido como `true` , a opção permite que o usuário restaure o dimensionamento de imagem herdado em monitores de DPI alto cuja escala seja definida como maior que 100%.</span><span class="sxs-lookup"><span data-stu-id="c16b8-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="c16b8-106">Para obter mais informações, consulte as [notas de versão do .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) no github.</span><span class="sxs-lookup"><span data-stu-id="c16b8-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="c16b8-107">No .NET Core, `Switch.System.Windows.Forms.UseLegacyImages` não há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="c16b8-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c16b8-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c16b8-108">Version introduced</span></span>

<span data-ttu-id="c16b8-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="c16b8-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c16b8-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="c16b8-110">Recommended action</span></span>

<span data-ttu-id="c16b8-111">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="c16b8-111">Remove the switch.</span></span> <span data-ttu-id="c16b8-112">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="c16b8-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="c16b8-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="c16b8-113">Category</span></span>

<span data-ttu-id="c16b8-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c16b8-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c16b8-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="c16b8-115">Affected APIs</span></span>

- <span data-ttu-id="c16b8-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c16b8-116">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
