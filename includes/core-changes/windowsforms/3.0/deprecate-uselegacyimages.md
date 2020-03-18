---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937063"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="b36fe-101">O switch de compatibilidade UseLegacyImages não é suportado</span><span class="sxs-lookup"><span data-stu-id="b36fe-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="b36fe-102">O `Switch.System.Windows.Forms.UseLegacyImages` switch de compatibilidade, que foi introduzido no .NET Framework 4.8, não é suportado no Windows Forms no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="b36fe-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b36fe-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="b36fe-103">Change description</span></span>

<span data-ttu-id="b36fe-104">Começando com o .NET Framework `Switch.System.Windows.Forms.UseLegacyImages` 4.8, o switch de compatibilidade abordou possíveis problemas de dimensionamento de imagem em cenários clickOnce em ambientes de DPI elevados.</span><span class="sxs-lookup"><span data-stu-id="b36fe-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="b36fe-105">Quando definido `true`para , o switch permite que o usuário restaure o dimensionamento de imagem legado em displays de DPI elevadocuja escala está definida como superior a 100%.</span><span class="sxs-lookup"><span data-stu-id="b36fe-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="b36fe-106">Para obter mais informações, consulte [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span><span class="sxs-lookup"><span data-stu-id="b36fe-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="b36fe-107">No .NET Core, o `Switch.System.Windows.Forms.UseLegacyImages` switch não é suportado.</span><span class="sxs-lookup"><span data-stu-id="b36fe-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b36fe-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b36fe-108">Version introduced</span></span>

<span data-ttu-id="b36fe-109">3.0 Visualização 9</span><span class="sxs-lookup"><span data-stu-id="b36fe-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b36fe-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b36fe-110">Recommended action</span></span>

<span data-ttu-id="b36fe-111">Remova o interruptor.</span><span class="sxs-lookup"><span data-stu-id="b36fe-111">Remove the switch.</span></span> <span data-ttu-id="b36fe-112">O switch não é suportado e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="b36fe-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="b36fe-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="b36fe-113">Category</span></span>

<span data-ttu-id="b36fe-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b36fe-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b36fe-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b36fe-115">Affected APIs</span></span>

- <span data-ttu-id="b36fe-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b36fe-116">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
