---
title: Redimensionar formulário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 8d4ce46ada505f952fc3090d10c5d893338d19f2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739309"
---
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="67aa6-102">Como redimensionar formulários do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67aa6-102">How to: Resize Windows Forms</span></span>

<span data-ttu-id="67aa6-103">Você pode especificar o tamanho do seu Windows Forms de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="67aa6-103">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="67aa6-104">Você pode alterar a altura e a largura do formulário programaticamente definindo um novo valor para a propriedade <xref:System.Windows.Forms.Form.Size%2A> ou ajustar as propriedades <xref:System.Windows.Forms.Control.Height%2A> ou <xref:System.Windows.Forms.Control.Width%2A> individualmente.</span><span class="sxs-lookup"><span data-stu-id="67aa6-104">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="67aa6-105">Se você estiver usando o Visual Studio, poderá alterar o tamanho usando o Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="67aa6-105">If you're using Visual Studio, you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="67aa6-106">Consulte também [Como redimensionar Windows Forms usando o Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="67aa6-106">Also see [How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span></span>

## <a name="resize-a-form-programmatically"></a><span data-ttu-id="67aa6-107">Redimensionar um formulário programaticamente</span><span class="sxs-lookup"><span data-stu-id="67aa6-107">Resize a form programmatically</span></span>

<span data-ttu-id="67aa6-108">Defina o tamanho de um formulário em tempo de execução definindo a propriedade <xref:System.Windows.Forms.Form.Size%2A> do formulário.</span><span class="sxs-lookup"><span data-stu-id="67aa6-108">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>

<span data-ttu-id="67aa6-109">O exemplo de código a seguir mostra o tamanho do formulário definido como 100 x 100 pixels.</span><span class="sxs-lookup"><span data-stu-id="67aa6-109">The following code example shows the form size set to 100 × 100 pixels.</span></span>

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a><span data-ttu-id="67aa6-110">Alterar a largura e a altura do formulário programaticamente</span><span class="sxs-lookup"><span data-stu-id="67aa6-110">Change form width and height programmatically</span></span>

<span data-ttu-id="67aa6-111">Depois que o <xref:System.Windows.Forms.Form.Size%2A> for definido, altere a altura ou a largura do formulário usando as propriedades <xref:System.Windows.Forms.Control.Width%2A> ou <xref:System.Windows.Forms.Control.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="67aa6-111">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

<span data-ttu-id="67aa6-112">O exemplo de código a seguir mostra a largura do formulário definida para 300 pixels da borda esquerda do formulário, enquanto a altura permanece constante.</span><span class="sxs-lookup"><span data-stu-id="67aa6-112">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

<span data-ttu-id="67aa6-113">- ou -</span><span class="sxs-lookup"><span data-stu-id="67aa6-113">-or-</span></span>

<span data-ttu-id="67aa6-114">Altere <xref:System.Drawing.Size.Width%2A> ou <xref:System.Drawing.Size.Height%2A> definindo a propriedade <xref:System.Windows.Forms.Form.Size%2A>.</span><span class="sxs-lookup"><span data-stu-id="67aa6-114">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>

<span data-ttu-id="67aa6-115">No entanto, como mostra o exemplo de código a seguir, essa abordagem é mais complicada do que apenas definir <xref:System.Windows.Forms.Control.Width%2A> ou <xref:System.Windows.Forms.Control.Height%2A> Propriedades.</span><span class="sxs-lookup"><span data-stu-id="67aa6-115">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a><span data-ttu-id="67aa6-116">Alterar o tamanho do formulário por incrementos programaticamente</span><span class="sxs-lookup"><span data-stu-id="67aa6-116">Change form size by increments programmatically</span></span>

<span data-ttu-id="67aa6-117">Para incrementar o tamanho do formulário, defina as propriedades <xref:System.Drawing.Size.Width%2A> e <xref:System.Drawing.Size.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="67aa6-117">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>

<span data-ttu-id="67aa6-118">O exemplo de código a seguir mostra a largura do formulário definida para 200 pixels mais larga do que a configuração atual.</span><span class="sxs-lookup"><span data-stu-id="67aa6-118">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>

```vb
Form1.Width += 200
```

```csharp
Form1.Width += 200;
```

```cpp
Form1->Width += 200;
```

> [!CAUTION]
> <span data-ttu-id="67aa6-119">Sempre use a propriedade <xref:System.Drawing.Size.Height%2A> ou <xref:System.Drawing.Size.Width%2A> para alterar uma dimensão de um formulário, a menos que você esteja definindo dimensões de altura e largura ao mesmo tempo definindo a propriedade <xref:System.Windows.Forms.Form.Size%2A> como uma nova estrutura de <xref:System.Drawing.Size>.</span><span class="sxs-lookup"><span data-stu-id="67aa6-119">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="67aa6-120">A propriedade <xref:System.Windows.Forms.Form.Size%2A> retorna uma estrutura de <xref:System.Drawing.Size>, que é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="67aa6-120">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="67aa6-121">Não é possível atribuir um novo valor para a propriedade de um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="67aa6-121">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="67aa6-122">Portanto, o código a seguir não será compilado.</span><span class="sxs-lookup"><span data-stu-id="67aa6-122">Therefore, the following code example will not compile.</span></span>

```vb
' NOTE: CODE WILL NOT COMPILE
Dim f As New Form()
f.Size.Width += 100
```

```csharp
// NOTE: CODE WILL NOT COMPILE
Form f = new Form();
f.Size.Width += 100;
```

```cpp
// NOTE: CODE WILL NOT COMPILE
Form^ f = gcnew Form();
f->Size->X += 100;
```

## <a name="see-also"></a><span data-ttu-id="67aa6-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="67aa6-123">See also</span></span>

- [<span data-ttu-id="67aa6-124">Introdução ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67aa6-124">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="67aa6-125">Aprimorando Aplicativos dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67aa6-125">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
