---
title: Objeto My. Forms (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 17042f60eb27c41640ef5d8c927c7acc5bc73183
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712609"
---
# <a name="myforms-object"></a><span data-ttu-id="bbbf8-102">Objeto My.Forms</span><span class="sxs-lookup"><span data-stu-id="bbbf8-102">My.Forms Object</span></span>
<span data-ttu-id="bbbf8-103">Fornece propriedades para acessar uma instância de cada formulário do Windows declarado no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbbf8-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="bbbf8-104">Remarks</span></span>  
 <span data-ttu-id="bbbf8-105">O `My.Forms` objeto fornece uma instância de cada formulário no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="bbbf8-106">O nome da propriedade é igual ao nome do formulário que acessa a propriedade.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-106">The name of the property is the same as the name of the form that the property accesses.</span></span>   
  
 <span data-ttu-id="bbbf8-107">Você pode acessar os formulários fornecidos pelo `My.Forms` objeto usando o nome do formulário, sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="bbbf8-108">Como o nome da propriedade é o mesmo nome do tipo do formulário, isso permite que você acesse um formulário como se tivesse uma instância padrão.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="bbbf8-109">Por exemplo, `My.Forms.Form1.Show` equivale a `Form1.Show`.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="bbbf8-110">O `My.Forms` objeto expõe apenas as formas associadas ao projeto atual.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="bbbf8-111">Ele não fornece acesso aos formulários declarados em DLLs referenciadas.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="bbbf8-112">Para acessar um formulário que fornece uma DLL, você deve usar o nome qualificado do formulário, escrito como *DllName*. *FormName*.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="bbbf8-113">Você pode usar o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> propriedade para obter uma coleção de todos os formulários abertos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="bbbf8-114">O objeto e suas propriedades estão disponíveis somente para aplicativos do Windows.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-114">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bbbf8-115">Propriedades</span><span class="sxs-lookup"><span data-stu-id="bbbf8-115">Properties</span></span>  
 <span data-ttu-id="bbbf8-116">Cada propriedade do `My.Forms` objeto fornece acesso a uma instância de um formulário no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="bbbf8-117">O nome da propriedade é igual ao nome do formulário que acessa a propriedade e o tipo de propriedade é o mesmo tipo do formulário.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbbf8-118">Se houver uma colisão de nomes, o nome da propriedade para acessar um formulário é *RootNamespace*_*Namespace*\_*FormName*.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="bbbf8-119">Por exemplo, considere dois formulários denominados `Form1.`se uma dessas formas está no namespace raiz `WindowsApplication1` e no namespace `Namespace1`, você poderá acessar esse formulário por meio de `My.Forms.WindowsApplication1_Namespace1_Form1`.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="bbbf8-120">O `My.Forms` objeto fornece acesso à instância do formulário principal do aplicativo criado na inicialização.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="bbbf8-121">Para todas as outras formas, o `My.Forms` objeto cria uma nova instância do formulário quando ele é acessado e os armazena.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="bbbf8-122">Tentativas subsequentes para acessar essa propriedade retornam essa instância do formulário.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-122">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="bbbf8-123">Você pode descartar um formulário por meio da atribuição `Nothing` à propriedade para esse formulário.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="bbbf8-124">A propriedade setter chama o <xref:System.Windows.Forms.Form.Close%2A> método de formulário e, em seguida, atribui `Nothing` ao valor armazenado.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="bbbf8-125">Se você atribuir qualquer valor diferente de `Nothing` à propriedade setter lança um <xref:System.ArgumentException> exceção.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="bbbf8-126">Você pode testar se uma propriedade do `My.Forms` objeto armazena uma instância do formulário usando o `Is` ou `IsNot` operador.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="bbbf8-127">Você pode usar esses operadores para verificar se o valor da propriedade é `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbbf8-128">Normalmente, o `Is` ou `IsNot` operador tem de ler o valor da propriedade para executar a comparação.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="bbbf8-129">No entanto, se a propriedade atualmente armazena `Nothing`, a propriedade cria uma nova instância do formulário e, em seguida, retorna essa instância.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="bbbf8-130">No entanto, o compilador do Visual Basic trata as propriedades do `My.Forms` diferentemente do objeto e permite que o `Is` ou `IsNot` operador para verificar o status da propriedade sem alterar seu valor.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbbf8-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bbbf8-131">Example</span></span>  
 <span data-ttu-id="bbbf8-132">Este exemplo altera o título padrão do `SidebarMenu` formulário.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-132">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 <span data-ttu-id="bbbf8-133">Para esse exemplo funcione, seu projeto deve ter um formulário chamado `SidebarMenu`.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>  
  
 <span data-ttu-id="bbbf8-134">Esse código funciona apenas em um projeto de aplicativo do Windows.</span><span class="sxs-lookup"><span data-stu-id="bbbf8-134">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbbf8-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bbbf8-135">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="bbbf8-136">Disponibilidade por tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="bbbf8-136">Availability by Project Type</span></span>  
  
|<span data-ttu-id="bbbf8-137">Tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="bbbf8-137">Project type</span></span>|<span data-ttu-id="bbbf8-138">Disponível</span><span class="sxs-lookup"><span data-stu-id="bbbf8-138">Available</span></span>|  
|---|---|  
|<span data-ttu-id="bbbf8-139">Aplicativo do Windows</span><span class="sxs-lookup"><span data-stu-id="bbbf8-139">Windows Application</span></span>|<span data-ttu-id="bbbf8-140">**Sim**</span><span class="sxs-lookup"><span data-stu-id="bbbf8-140">**Yes**</span></span>|  
|<span data-ttu-id="bbbf8-141">Biblioteca de Classes</span><span class="sxs-lookup"><span data-stu-id="bbbf8-141">Class Library</span></span>|<span data-ttu-id="bbbf8-142">Não</span><span class="sxs-lookup"><span data-stu-id="bbbf8-142">No</span></span>|  
|<span data-ttu-id="bbbf8-143">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="bbbf8-143">Console Application</span></span>|<span data-ttu-id="bbbf8-144">Não</span><span class="sxs-lookup"><span data-stu-id="bbbf8-144">No</span></span>|  
|<span data-ttu-id="bbbf8-145">Biblioteca de controle do Windows</span><span class="sxs-lookup"><span data-stu-id="bbbf8-145">Windows Control Library</span></span>|<span data-ttu-id="bbbf8-146">Não</span><span class="sxs-lookup"><span data-stu-id="bbbf8-146">No</span></span>|  
|<span data-ttu-id="bbbf8-147">Biblioteca de controle da Web</span><span class="sxs-lookup"><span data-stu-id="bbbf8-147">Web Control Library</span></span>|<span data-ttu-id="bbbf8-148">Não</span><span class="sxs-lookup"><span data-stu-id="bbbf8-148">No</span></span>|  
|<span data-ttu-id="bbbf8-149">Serviço do Windows</span><span class="sxs-lookup"><span data-stu-id="bbbf8-149">Windows Service</span></span>|<span data-ttu-id="bbbf8-150">Não</span><span class="sxs-lookup"><span data-stu-id="bbbf8-150">No</span></span>|  
|<span data-ttu-id="bbbf8-151">Site da Web</span><span class="sxs-lookup"><span data-stu-id="bbbf8-151">Web Site</span></span>|<span data-ttu-id="bbbf8-152">Não</span><span class="sxs-lookup"><span data-stu-id="bbbf8-152">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bbbf8-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbbf8-153">See also</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [<span data-ttu-id="bbbf8-154">Objetos</span><span class="sxs-lookup"><span data-stu-id="bbbf8-154">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)
- [<span data-ttu-id="bbbf8-155">Operador Is</span><span class="sxs-lookup"><span data-stu-id="bbbf8-155">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="bbbf8-156">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="bbbf8-156">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="bbbf8-157">Acessando formulários de aplicativo</span><span class="sxs-lookup"><span data-stu-id="bbbf8-157">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
