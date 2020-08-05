---
ms.openlocfilehash: d69f619522c7abc3171f1c089e53cc2754899f93
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556120"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="aaf16-101">Não há suporte para a opção de compatibilidade UseLegacyImages</span><span class="sxs-lookup"><span data-stu-id="aaf16-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="aaf16-102">A `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade, que foi introduzida no .NET Framework 4,8, não tem suporte no Windows Forms no .NET Core ou no .net 5,0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="aaf16-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="aaf16-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="aaf16-103">Change description</span></span>

<span data-ttu-id="aaf16-104">A partir do .NET Framework 4,8, a `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade resolveu possíveis problemas de dimensionamento de imagem em cenários de ClickOnce em ambientes de DPI alto.</span><span class="sxs-lookup"><span data-stu-id="aaf16-104">Starting with .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="aaf16-105">Quando definido como `true` , a opção permite que o usuário restaure o dimensionamento de imagem herdado em monitores de DPI alto cuja escala seja definida como maior que 100%.</span><span class="sxs-lookup"><span data-stu-id="aaf16-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="aaf16-106">Para obter mais informações, consulte as [notas de versão do .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) no github.</span><span class="sxs-lookup"><span data-stu-id="aaf16-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="aaf16-107">No .NET Core e no .NET 5,0 e posterior, `Switch.System.Windows.Forms.UseLegacyImages` não há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="aaf16-107">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="aaf16-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="aaf16-108">Version introduced</span></span>

<span data-ttu-id="aaf16-109">3.0</span><span class="sxs-lookup"><span data-stu-id="aaf16-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="aaf16-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="aaf16-110">Recommended action</span></span>

<span data-ttu-id="aaf16-111">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="aaf16-111">Remove the switch.</span></span> <span data-ttu-id="aaf16-112">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="aaf16-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="aaf16-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="aaf16-113">Category</span></span>

<span data-ttu-id="aaf16-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aaf16-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aaf16-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="aaf16-115">Affected APIs</span></span>

- <span data-ttu-id="aaf16-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="aaf16-116">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
