---
ms.openlocfilehash: 07527c247e6ccd53d2a77793946ffc796c3e1cbb
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181747"
---
### <a name="switchsystemwindowsformsuselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="98497-101">Não há suporte para a opção de compatibilidade switch. System. Windows. Forms. UseLegacyImages</span><span class="sxs-lookup"><span data-stu-id="98497-101">Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="98497-102">A `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade, que foi introduzida no .NET Framework 4,8, não tem suporte no Windows Forms no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="98497-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="98497-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="98497-103">Change description</span></span>

<span data-ttu-id="98497-104">A partir do .NET Framework 4,8, a `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade resolveu possíveis problemas de dimensionamento de imagem em cenários de ClickOnce em ambientes de DPI alto.</span><span class="sxs-lookup"><span data-stu-id="98497-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="98497-105">Quando definido como `true`, a opção permite que o usuário restaure o dimensionamento de imagem herdado em monitores de DPI alto cuja escala seja definida como maior que 100%.</span><span class="sxs-lookup"><span data-stu-id="98497-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="98497-106">Para obter mais informações, consulte as [notas de versão do .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) no github.</span><span class="sxs-lookup"><span data-stu-id="98497-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="98497-107">No .NET Core, não `Switch.System.Windows.Forms.UseLegacyImages` há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="98497-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="98497-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="98497-108">Version introduced</span></span>

<span data-ttu-id="98497-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="98497-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="98497-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="98497-110">Recommended action</span></span>

<span data-ttu-id="98497-111">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="98497-111">Remove the switch.</span></span> <span data-ttu-id="98497-112">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="98497-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="98497-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="98497-113">Category</span></span>

<span data-ttu-id="98497-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="98497-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="98497-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="98497-115">Affected APIs</span></span>

- <span data-ttu-id="98497-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="98497-116">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
