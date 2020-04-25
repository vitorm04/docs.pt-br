---
ms.openlocfilehash: 5212c5d9513a8ef5f51693857d0ddb60db4e49b9
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158380"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="395ec-101">Os métodos WinForms agora lançam ArgumentException</span><span class="sxs-lookup"><span data-stu-id="395ec-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="395ec-102">Alguns métodos de Windows Forms agora lançam um <xref:System.ArgumentException> para argumentos inválidos, onde anteriormente não fizeram isso.</span><span class="sxs-lookup"><span data-stu-id="395ec-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="395ec-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="395ec-103">Change description</span></span>

<span data-ttu-id="395ec-104">Anteriormente, passar argumentos de um tipo inesperado ou incorreto para determinados métodos de Windows Forms resultaria em um estado indeterminado.</span><span class="sxs-lookup"><span data-stu-id="395ec-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="395ec-105">A partir do .NET 5,0, esses métodos agora geram um <xref:System.ArgumentException> quando passaram argumentos inválidos.</span><span class="sxs-lookup"><span data-stu-id="395ec-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="395ec-106">Lançar um <xref:System.ArgumentException> está em conformidade com o comportamento do tempo de execução do .net.</span><span class="sxs-lookup"><span data-stu-id="395ec-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="395ec-107">Ele também melhora a experiência de depuração ao comunicar-se claramente qual argumento é inválido.</span><span class="sxs-lookup"><span data-stu-id="395ec-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

<span data-ttu-id="395ec-108">A tabela a seguir lista os métodos e parâmetros afetados:</span><span class="sxs-lookup"><span data-stu-id="395ec-108">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="395ec-109">Método</span><span class="sxs-lookup"><span data-stu-id="395ec-109">Method</span></span> | <span data-ttu-id="395ec-110">Nome do parâmetro</span><span class="sxs-lookup"><span data-stu-id="395ec-110">Parameter name</span></span> | <span data-ttu-id="395ec-111">Condição</span><span class="sxs-lookup"><span data-stu-id="395ec-111">Condition</span></span> | <span data-ttu-id="395ec-112">Versão adicionada</span><span class="sxs-lookup"><span data-stu-id="395ec-112">Version added</span></span> |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="395ec-113">O argumento não é do <xref:System.Windows.Forms.TabPage>tipo.</span><span class="sxs-lookup"><span data-stu-id="395ec-113">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="395ec-114">5,0 visualização 1</span><span class="sxs-lookup"><span data-stu-id="395ec-114">5.0 Preview 1</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="395ec-115">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="395ec-115">Version introduced</span></span>

<span data-ttu-id="395ec-116">.NET 5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="395ec-116">.NET 5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="395ec-117">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="395ec-117">Recommended action</span></span>

- <span data-ttu-id="395ec-118">Atualize o código para evitar a passagem de argumentos inválidos.</span><span class="sxs-lookup"><span data-stu-id="395ec-118">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="395ec-119">Se necessário, manipule um <xref:System.ArgumentException> ao chamar o método.</span><span class="sxs-lookup"><span data-stu-id="395ec-119">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="395ec-120">Categoria</span><span class="sxs-lookup"><span data-stu-id="395ec-120">Category</span></span>

<span data-ttu-id="395ec-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="395ec-121">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="395ec-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="395ec-122">Affected APIs</span></span>

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->
