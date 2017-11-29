---
title: Objeto My.Forms
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords: My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a5aa7af1f07a29660335d968c1ecc17be5f8beec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="myforms-object"></a><span data-ttu-id="5dfdc-102">Objeto My.Forms</span><span class="sxs-lookup"><span data-stu-id="5dfdc-102">My.Forms Object</span></span>
<span data-ttu-id="5dfdc-103">Fornece propriedades para acessar uma instância de cada Windows form declarado no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5dfdc-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="5dfdc-104">Remarks</span></span>  
 <span data-ttu-id="5dfdc-105">O `My.Forms` objeto fornece uma instância de cada formulário no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="5dfdc-106">O nome da propriedade é igual ao nome do formulário que acessa a propriedade.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-106">The name of the property is the same as the name of the form that the property accesses.</span></span> <span data-ttu-id="5dfdc-107">Para obter informações sobre como adicionar formas a um projeto, consulte [como: adicionar formulários do Windows para um projeto](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="5dfdc-107">For information about adding forms to a project, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="5dfdc-108">Você pode acessar os formulários fornecidos pelo `My.Forms` objeto usando o nome do formulário, sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-108">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="5dfdc-109">Como o nome da propriedade é o mesmo nome do tipo do formulário, isso permite que você acesse um formulário como se tivesse uma instância padrão.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-109">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="5dfdc-110">Por exemplo, `My.Forms.Form1.Show` equivale a `Form1.Show`.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-110">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="5dfdc-111">O `My.Forms` objeto expõe apenas aos formulários associados ao projeto atual.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-111">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="5dfdc-112">Ele não fornece acesso aos formulários declarado em DLLs referenciados.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-112">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="5dfdc-113">Para acessar um formulário que fornece uma DLL, você deve usar o nome qualificado do formulário, gravado como *Nomedadll*. *Nome do formulário*.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-113">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="5dfdc-114">Você pode usar o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> propriedade para obter uma coleção de todos os formulários do aplicativo aberto.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-114">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="5dfdc-115">O objeto e suas propriedades estão disponíveis apenas para aplicativos do Windows.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-115">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5dfdc-116">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5dfdc-116">Properties</span></span>  
 <span data-ttu-id="5dfdc-117">Cada propriedade do `My.Forms` objeto fornece acesso a uma instância de um formulário no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-117">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="5dfdc-118">O nome da propriedade é igual ao nome do formulário que acessa a propriedade e o tipo de propriedade é o mesmo tipo do formulário.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-118">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5dfdc-119">Se houver uma colisão de nomes, o nome da propriedade para acessar um formulário é *RootNamespace*_*Namespace*\_*nome do formulário*.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-119">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="5dfdc-120">Por exemplo, considere duas formas denominadas `Form1.`se uma dessas formas está no namespace raiz `WindowsApplication1` e no namespace `Namespace1`, você acessaria o formulário por meio de `My.Forms.WindowsApplication1_Namespace1_Form1`.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-120">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="5dfdc-121">O `My.Forms` objeto fornece acesso à instância do formulário principal do aplicativo, que foi criada na inicialização.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-121">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="5dfdc-122">Para todas as outras formas de `My.Forms` objeto cria uma nova instância do formulário quando ele é acessado e os armazena.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-122">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="5dfdc-123">As tentativas subsequentes para acessar essa propriedade retornam essa instância do formulário.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-123">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="5dfdc-124">Você pode descartar um formulário atribuindo `Nothing` para a propriedade para esse formulário.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-124">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="5dfdc-125">A propriedade setter chama o <xref:System.Windows.Forms.Form.Close%2A> método de formulário e, em seguida, atribui `Nothing` ao valor armazenado.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-125">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="5dfdc-126">Se você atribuir qualquer valor diferente de `Nothing` para a propriedade setter lança um <xref:System.ArgumentException> exceção.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="5dfdc-127">Você pode testar se uma propriedade do `My.Forms` objeto armazena uma instância do formulário usando o `Is` ou `IsNot` operador.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-127">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="5dfdc-128">Você pode usar os operadores para verificar se o valor da propriedade é `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5dfdc-129">Normalmente, o `Is` ou `IsNot` operador precisa ler o valor da propriedade para executar a comparação.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="5dfdc-130">No entanto, se a propriedade armazena atualmente `Nothing`, a propriedade cria uma nova instância do formulário e, em seguida, retorna essa instância.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-130">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="5dfdc-131">No entanto, o compilador do Visual Basic trata as propriedades do `My.Forms` diferente do objeto e permite que o `Is` ou `IsNot` operador para verificar o status da propriedade sem alterar seu valor.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-131">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5dfdc-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5dfdc-132">Example</span></span>  
 <span data-ttu-id="5dfdc-133">Este exemplo altera o título do padrão `SidebarMenu` formulário.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-133">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 <span data-ttu-id="5dfdc-134">Para esse exemplo funcione, seu projeto deve ter um formulário denominado `SidebarMenu`.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-134">For this example to work, your project must have a form named `SidebarMenu`.</span></span> <span data-ttu-id="5dfdc-135">Para obter mais informações, consulte [Como adicionar o Windows Forms a um projeto](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="5dfdc-135">For more information, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="5dfdc-136">Esse código funcionará somente em um projeto de aplicativo do Windows.</span><span class="sxs-lookup"><span data-stu-id="5dfdc-136">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dfdc-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5dfdc-137">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="5dfdc-138">Disponibilidade por tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="5dfdc-138">Availability by Project Type</span></span>  
  
|<span data-ttu-id="5dfdc-139">Tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="5dfdc-139">Project type</span></span>|<span data-ttu-id="5dfdc-140">Disponível</span><span class="sxs-lookup"><span data-stu-id="5dfdc-140">Available</span></span>|  
|---|---|  
|<span data-ttu-id="5dfdc-141">Aplicativo do Windows</span><span class="sxs-lookup"><span data-stu-id="5dfdc-141">Windows Application</span></span>|<span data-ttu-id="5dfdc-142">**Sim**</span><span class="sxs-lookup"><span data-stu-id="5dfdc-142">**Yes**</span></span>|  
|<span data-ttu-id="5dfdc-143">Biblioteca de Classes</span><span class="sxs-lookup"><span data-stu-id="5dfdc-143">Class Library</span></span>|<span data-ttu-id="5dfdc-144">Não</span><span class="sxs-lookup"><span data-stu-id="5dfdc-144">No</span></span>|  
|<span data-ttu-id="5dfdc-145">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="5dfdc-145">Console Application</span></span>|<span data-ttu-id="5dfdc-146">Não</span><span class="sxs-lookup"><span data-stu-id="5dfdc-146">No</span></span>|  
|<span data-ttu-id="5dfdc-147">Biblioteca de controle do Windows</span><span class="sxs-lookup"><span data-stu-id="5dfdc-147">Windows Control Library</span></span>|<span data-ttu-id="5dfdc-148">Não</span><span class="sxs-lookup"><span data-stu-id="5dfdc-148">No</span></span>|  
|<span data-ttu-id="5dfdc-149">Biblioteca de controle da Web</span><span class="sxs-lookup"><span data-stu-id="5dfdc-149">Web Control Library</span></span>|<span data-ttu-id="5dfdc-150">Não</span><span class="sxs-lookup"><span data-stu-id="5dfdc-150">No</span></span>|  
|<span data-ttu-id="5dfdc-151">Serviço do Windows</span><span class="sxs-lookup"><span data-stu-id="5dfdc-151">Windows Service</span></span>|<span data-ttu-id="5dfdc-152">Não</span><span class="sxs-lookup"><span data-stu-id="5dfdc-152">No</span></span>|  
|<span data-ttu-id="5dfdc-153">Site da Web</span><span class="sxs-lookup"><span data-stu-id="5dfdc-153">Web Site</span></span>|<span data-ttu-id="5dfdc-154">Não</span><span class="sxs-lookup"><span data-stu-id="5dfdc-154">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5dfdc-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5dfdc-155">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [<span data-ttu-id="5dfdc-156">Objetos</span><span class="sxs-lookup"><span data-stu-id="5dfdc-156">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)  
 [<span data-ttu-id="5dfdc-157">Como: adicionar formulários do Windows a um projeto</span><span class="sxs-lookup"><span data-stu-id="5dfdc-157">How to: Add Windows Forms to a Project</span></span>](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)  
 [<span data-ttu-id="5dfdc-158">Operador Is</span><span class="sxs-lookup"><span data-stu-id="5dfdc-158">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="5dfdc-159">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="5dfdc-159">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="5dfdc-160">Acessando formulários de aplicativo</span><span class="sxs-lookup"><span data-stu-id="5dfdc-160">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
