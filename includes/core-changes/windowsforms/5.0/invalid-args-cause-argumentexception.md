---
ms.openlocfilehash: 9f6703c77e17ac9376aee944b891f4635dc7632e
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309125"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="04318-101">Os métodos WinForms agora lançam ArgumentException</span><span class="sxs-lookup"><span data-stu-id="04318-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="04318-102">Alguns métodos de Windows Forms agora lançam um <xref:System.ArgumentException> para argumentos inválidos, onde anteriormente não fizeram isso.</span><span class="sxs-lookup"><span data-stu-id="04318-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="04318-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="04318-103">Change description</span></span>

<span data-ttu-id="04318-104">Anteriormente, passar argumentos de um tipo inesperado ou incorreto para determinados métodos de Windows Forms resultaria em um estado indeterminado.</span><span class="sxs-lookup"><span data-stu-id="04318-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="04318-105">A partir do .NET 5,0, esses métodos agora geram um <xref:System.ArgumentException> quando passaram argumentos inválidos.</span><span class="sxs-lookup"><span data-stu-id="04318-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="04318-106">Lançar um <xref:System.ArgumentException> está em conformidade com o comportamento do tempo de execução do .net.</span><span class="sxs-lookup"><span data-stu-id="04318-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="04318-107">Ele também melhora a experiência de depuração ao comunicar-se claramente qual argumento é inválido.</span><span class="sxs-lookup"><span data-stu-id="04318-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="04318-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="04318-108">Version introduced</span></span>

<span data-ttu-id="04318-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="04318-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="04318-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="04318-110">Recommended action</span></span>

- <span data-ttu-id="04318-111">Atualize o código para evitar a passagem de argumentos inválidos.</span><span class="sxs-lookup"><span data-stu-id="04318-111">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="04318-112">Se necessário, manipule um <xref:System.ArgumentException> ao chamar o método.</span><span class="sxs-lookup"><span data-stu-id="04318-112">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="04318-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="04318-113">Category</span></span>

<span data-ttu-id="04318-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="04318-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="04318-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="04318-115">Affected APIs</span></span>

<span data-ttu-id="04318-116">A tabela a seguir lista os métodos e parâmetros afetados:</span><span class="sxs-lookup"><span data-stu-id="04318-116">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="04318-117">Método</span><span class="sxs-lookup"><span data-stu-id="04318-117">Method</span></span> | <span data-ttu-id="04318-118">Nome do parâmetro</span><span class="sxs-lookup"><span data-stu-id="04318-118">Parameter name</span></span> | <span data-ttu-id="04318-119">Condição</span><span class="sxs-lookup"><span data-stu-id="04318-119">Condition</span></span> | <span data-ttu-id="04318-120">Versão adicionada</span><span class="sxs-lookup"><span data-stu-id="04318-120">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="04318-121">O argumento não é do tipo <xref:System.Windows.Forms.TabPage> .</span><span class="sxs-lookup"><span data-stu-id="04318-121">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="04318-122">Preview 1</span><span class="sxs-lookup"><span data-stu-id="04318-122">Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="04318-123">Argumento é `null` , <xref:System.String.Empty?displayProperty=nameWithType> ou espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="04318-123">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="04318-124">Versão prévia 5</span><span class="sxs-lookup"><span data-stu-id="04318-124">Preview 5</span></span> |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | <span data-ttu-id="04318-125">Não é possível recuperar um `InputLanguage` para a cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="04318-125">Unable to retrieve an `InputLanguage` for the specified culture.</span></span> | <span data-ttu-id="04318-126">Versão prévia 7</span><span class="sxs-lookup"><span data-stu-id="04318-126">Preview 7</span></span> |

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

-->
