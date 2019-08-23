---
title: Objeto My. Forms (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 9fa5c77dd12c98100e3d17fc473a6802180d1e32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965976"
---
# <a name="myforms-object"></a><span data-ttu-id="ccde4-102">Objeto My.Forms</span><span class="sxs-lookup"><span data-stu-id="ccde4-102">My.Forms Object</span></span>
<span data-ttu-id="ccde4-103">Fornece propriedades para acessar uma instância de cada formulário do Windows declarado no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="ccde4-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccde4-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="ccde4-104">Remarks</span></span>  
 <span data-ttu-id="ccde4-105">O `My.Forms` objeto fornece uma instância de cada formulário no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="ccde4-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="ccde4-106">O nome da propriedade é o mesmo que o nome do formulário que a propriedade acessa.</span><span class="sxs-lookup"><span data-stu-id="ccde4-106">The name of the property is the same as the name of the form that the property accesses.</span></span>   
  
 <span data-ttu-id="ccde4-107">Você pode acessar os formulários fornecidos pelo `My.Forms` objeto usando o nome do formulário, sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="ccde4-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="ccde4-108">Como o nome da propriedade é igual ao nome do tipo do formulário, isso permite que você acesse um formulário como se ele tivesse uma instância padrão.</span><span class="sxs-lookup"><span data-stu-id="ccde4-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="ccde4-109">Por exemplo, `My.Forms.Form1.Show` equivale a `Form1.Show`.</span><span class="sxs-lookup"><span data-stu-id="ccde4-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="ccde4-110">O `My.Forms` objeto expõe apenas os formulários associados ao projeto atual.</span><span class="sxs-lookup"><span data-stu-id="ccde4-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="ccde4-111">Ele não fornece acesso a formulários declarados em DLLs referenciadas.</span><span class="sxs-lookup"><span data-stu-id="ccde4-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="ccde4-112">Para acessar um formulário que uma DLL fornece, você deve usar o nome qualificado do formulário, escrito como *DllName*. *FormName*.</span><span class="sxs-lookup"><span data-stu-id="ccde4-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="ccde4-113">Você pode usar a <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> propriedade para obter uma coleção de todos os formulários abertos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ccde4-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="ccde4-114">O objeto e suas propriedades estão disponíveis apenas para aplicativos do Windows.</span><span class="sxs-lookup"><span data-stu-id="ccde4-114">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ccde4-115">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ccde4-115">Properties</span></span>  
 <span data-ttu-id="ccde4-116">Cada propriedade do `My.Forms` objeto fornece acesso a uma instância de um formulário no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="ccde4-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="ccde4-117">O nome da propriedade é o mesmo que o nome do formulário que a propriedade acessa, e o tipo de propriedade é o mesmo que o tipo do formulário.</span><span class="sxs-lookup"><span data-stu-id="ccde4-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ccde4-118">Se houver uma colisão de nomes, o nome da propriedade para acessar um formulário será *RootNamespace*_*namespace*\_*FormName*.</span><span class="sxs-lookup"><span data-stu-id="ccde4-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="ccde4-119">Por exemplo, considere dois formulários chamados `Form1.`se um desses formulários estiver no namespace `WindowsApplication1` raiz e no namespace `Namespace1`, você acessaria esse formulário por meio `My.Forms.WindowsApplication1_Namespace1_Form1`do.</span><span class="sxs-lookup"><span data-stu-id="ccde4-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="ccde4-120">O `My.Forms` objeto fornece acesso à instância do formulário principal do aplicativo que foi criado na inicialização.</span><span class="sxs-lookup"><span data-stu-id="ccde4-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="ccde4-121">Para todos os outros formulários, `My.Forms` o objeto cria uma nova instância do formulário quando ele é acessado e armazena-o.</span><span class="sxs-lookup"><span data-stu-id="ccde4-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="ccde4-122">As tentativas subsequentes de acessar essa propriedade retornam essa instância do formulário.</span><span class="sxs-lookup"><span data-stu-id="ccde4-122">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="ccde4-123">Você pode descartar um formulário atribuindo `Nothing` à propriedade para esse formulário.</span><span class="sxs-lookup"><span data-stu-id="ccde4-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="ccde4-124">O setter da propriedade chama <xref:System.Windows.Forms.Form.Close%2A> o método do formulário e, em seguida, `Nothing` atribui ao valor armazenado.</span><span class="sxs-lookup"><span data-stu-id="ccde4-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="ccde4-125">Se você atribuir qualquer valor diferente `Nothing` de à propriedade, o setter lançará uma <xref:System.ArgumentException> exceção.</span><span class="sxs-lookup"><span data-stu-id="ccde4-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="ccde4-126">Você pode testar se uma propriedade do `My.Forms` objeto armazena uma instância do formulário usando o `Is` operador or `IsNot` .</span><span class="sxs-lookup"><span data-stu-id="ccde4-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="ccde4-127">Você pode usar esses operadores para verificar se o valor da propriedade é `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ccde4-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ccde4-128">Normalmente, o `Is` operador `IsNot` or precisa ler o valor da propriedade para executar a comparação.</span><span class="sxs-lookup"><span data-stu-id="ccde4-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="ccde4-129">No entanto, se a propriedade `Nothing`atualmente armazena, a propriedade cria uma nova instância do formulário e, em seguida, retorna essa instância.</span><span class="sxs-lookup"><span data-stu-id="ccde4-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="ccde4-130">No entanto, o compilador de Visual Basic trata as `My.Forms` Propriedades do objeto de forma `Is` diferente `IsNot` e permite que o operador OR Verifique o status da propriedade sem alterar seu valor.</span><span class="sxs-lookup"><span data-stu-id="ccde4-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccde4-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ccde4-131">Example</span></span>  
 <span data-ttu-id="ccde4-132">Este exemplo altera o título do formulário padrão `SidebarMenu` .</span><span class="sxs-lookup"><span data-stu-id="ccde4-132">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]  
  
 <span data-ttu-id="ccde4-133">Para que este exemplo funcione, seu projeto deve ter um formulário chamado `SidebarMenu`.</span><span class="sxs-lookup"><span data-stu-id="ccde4-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>  
  
 <span data-ttu-id="ccde4-134">Esse código só funcionará em um projeto de aplicativo do Windows.</span><span class="sxs-lookup"><span data-stu-id="ccde4-134">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccde4-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ccde4-135">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="ccde4-136">Disponibilidade por tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="ccde4-136">Availability by Project Type</span></span>  
  
|<span data-ttu-id="ccde4-137">Tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="ccde4-137">Project type</span></span>|<span data-ttu-id="ccde4-138">Disponível</span><span class="sxs-lookup"><span data-stu-id="ccde4-138">Available</span></span>|  
|---|---|  
|<span data-ttu-id="ccde4-139">Aplicativo do Windows</span><span class="sxs-lookup"><span data-stu-id="ccde4-139">Windows Application</span></span>|<span data-ttu-id="ccde4-140">**Sim**</span><span class="sxs-lookup"><span data-stu-id="ccde4-140">**Yes**</span></span>|  
|<span data-ttu-id="ccde4-141">Biblioteca de Classes</span><span class="sxs-lookup"><span data-stu-id="ccde4-141">Class Library</span></span>|<span data-ttu-id="ccde4-142">Não</span><span class="sxs-lookup"><span data-stu-id="ccde4-142">No</span></span>|  
|<span data-ttu-id="ccde4-143">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="ccde4-143">Console Application</span></span>|<span data-ttu-id="ccde4-144">Não</span><span class="sxs-lookup"><span data-stu-id="ccde4-144">No</span></span>|  
|<span data-ttu-id="ccde4-145">Biblioteca de controle do Windows</span><span class="sxs-lookup"><span data-stu-id="ccde4-145">Windows Control Library</span></span>|<span data-ttu-id="ccde4-146">Não</span><span class="sxs-lookup"><span data-stu-id="ccde4-146">No</span></span>|  
|<span data-ttu-id="ccde4-147">Biblioteca de controle da Web</span><span class="sxs-lookup"><span data-stu-id="ccde4-147">Web Control Library</span></span>|<span data-ttu-id="ccde4-148">Não</span><span class="sxs-lookup"><span data-stu-id="ccde4-148">No</span></span>|  
|<span data-ttu-id="ccde4-149">Serviço do Windows</span><span class="sxs-lookup"><span data-stu-id="ccde4-149">Windows Service</span></span>|<span data-ttu-id="ccde4-150">Não</span><span class="sxs-lookup"><span data-stu-id="ccde4-150">No</span></span>|  
|<span data-ttu-id="ccde4-151">Site da Web</span><span class="sxs-lookup"><span data-stu-id="ccde4-151">Web Site</span></span>|<span data-ttu-id="ccde4-152">Não</span><span class="sxs-lookup"><span data-stu-id="ccde4-152">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccde4-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccde4-153">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [<span data-ttu-id="ccde4-154">Objetos</span><span class="sxs-lookup"><span data-stu-id="ccde4-154">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)
- [<span data-ttu-id="ccde4-155">Operador Is</span><span class="sxs-lookup"><span data-stu-id="ccde4-155">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="ccde4-156">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="ccde4-156">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="ccde4-157">Acessando formulários de aplicativo</span><span class="sxs-lookup"><span data-stu-id="ccde4-157">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
