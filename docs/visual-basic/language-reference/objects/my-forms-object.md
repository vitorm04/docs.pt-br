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
ms.openlocfilehash: fe548caacf2c8e7498e3b7abc814b4f89af9b3d6
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="myforms-object"></a><span data-ttu-id="1728f-102">Objeto My.Forms</span><span class="sxs-lookup"><span data-stu-id="1728f-102">My.Forms Object</span></span>
<span data-ttu-id="1728f-103">Fornece propriedades para acessar uma instância de cada Windows form declarado no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="1728f-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1728f-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="1728f-104">Remarks</span></span>  
 <span data-ttu-id="1728f-105">O `My.Forms` objeto fornece uma instância de cada formulário no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="1728f-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="1728f-106">O nome da propriedade é igual ao nome do formulário que acessa a propriedade.</span><span class="sxs-lookup"><span data-stu-id="1728f-106">The name of the property is the same as the name of the form that the property accesses.</span></span>   
  
 <span data-ttu-id="1728f-107">Você pode acessar os formulários fornecidos pelo `My.Forms` objeto usando o nome do formulário, sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="1728f-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="1728f-108">Como o nome da propriedade é o mesmo nome do tipo do formulário, isso permite que você acesse um formulário como se tivesse uma instância padrão.</span><span class="sxs-lookup"><span data-stu-id="1728f-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="1728f-109">Por exemplo, `My.Forms.Form1.Show` equivale a `Form1.Show`.</span><span class="sxs-lookup"><span data-stu-id="1728f-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="1728f-110">O `My.Forms` objeto expõe apenas aos formulários associados ao projeto atual.</span><span class="sxs-lookup"><span data-stu-id="1728f-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="1728f-111">Ele não fornece acesso aos formulários declarado em DLLs referenciados.</span><span class="sxs-lookup"><span data-stu-id="1728f-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="1728f-112">Para acessar um formulário que fornece uma DLL, você deve usar o nome qualificado do formulário, gravado como *Nomedadll*. *Nome do formulário*.</span><span class="sxs-lookup"><span data-stu-id="1728f-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="1728f-113">Você pode usar o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> propriedade para obter uma coleção de todos os formulários do aplicativo aberto.</span><span class="sxs-lookup"><span data-stu-id="1728f-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="1728f-114">O objeto e suas propriedades estão disponíveis apenas para aplicativos do Windows.</span><span class="sxs-lookup"><span data-stu-id="1728f-114">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1728f-115">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1728f-115">Properties</span></span>  
 <span data-ttu-id="1728f-116">Cada propriedade do `My.Forms` objeto fornece acesso a uma instância de um formulário no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="1728f-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="1728f-117">O nome da propriedade é igual ao nome do formulário que acessa a propriedade e o tipo de propriedade é o mesmo tipo do formulário.</span><span class="sxs-lookup"><span data-stu-id="1728f-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1728f-118">Se houver uma colisão de nomes, o nome da propriedade para acessar um formulário é *RootNamespace*_*Namespace*\_*nome do formulário*.</span><span class="sxs-lookup"><span data-stu-id="1728f-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="1728f-119">Por exemplo, considere duas formas denominadas `Form1.`se uma dessas formas está no namespace raiz `WindowsApplication1` e no namespace `Namespace1`, você acessaria o formulário por meio de `My.Forms.WindowsApplication1_Namespace1_Form1`.</span><span class="sxs-lookup"><span data-stu-id="1728f-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="1728f-120">O `My.Forms` objeto fornece acesso à instância do formulário principal do aplicativo, que foi criada na inicialização.</span><span class="sxs-lookup"><span data-stu-id="1728f-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="1728f-121">Para todas as outras formas de `My.Forms` objeto cria uma nova instância do formulário quando ele é acessado e os armazena.</span><span class="sxs-lookup"><span data-stu-id="1728f-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="1728f-122">As tentativas subsequentes para acessar essa propriedade retornam essa instância do formulário.</span><span class="sxs-lookup"><span data-stu-id="1728f-122">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="1728f-123">Você pode descartar um formulário atribuindo `Nothing` para a propriedade para esse formulário.</span><span class="sxs-lookup"><span data-stu-id="1728f-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="1728f-124">A propriedade setter chama o <xref:System.Windows.Forms.Form.Close%2A> método de formulário e, em seguida, atribui `Nothing` ao valor armazenado.</span><span class="sxs-lookup"><span data-stu-id="1728f-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="1728f-125">Se você atribuir qualquer valor diferente de `Nothing` para a propriedade setter lança um <xref:System.ArgumentException> exceção.</span><span class="sxs-lookup"><span data-stu-id="1728f-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="1728f-126">Você pode testar se uma propriedade do `My.Forms` objeto armazena uma instância do formulário usando o `Is` ou `IsNot` operador.</span><span class="sxs-lookup"><span data-stu-id="1728f-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="1728f-127">Você pode usar os operadores para verificar se o valor da propriedade é `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="1728f-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1728f-128">Normalmente, o `Is` ou `IsNot` operador precisa ler o valor da propriedade para executar a comparação.</span><span class="sxs-lookup"><span data-stu-id="1728f-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="1728f-129">No entanto, se a propriedade armazena atualmente `Nothing`, a propriedade cria uma nova instância do formulário e, em seguida, retorna essa instância.</span><span class="sxs-lookup"><span data-stu-id="1728f-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="1728f-130">No entanto, o compilador do Visual Basic trata as propriedades do `My.Forms` diferente do objeto e permite que o `Is` ou `IsNot` operador para verificar o status da propriedade sem alterar seu valor.</span><span class="sxs-lookup"><span data-stu-id="1728f-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1728f-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1728f-131">Example</span></span>  
 <span data-ttu-id="1728f-132">Este exemplo altera o título do padrão `SidebarMenu` formulário.</span><span class="sxs-lookup"><span data-stu-id="1728f-132">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 <span data-ttu-id="1728f-133">Para esse exemplo funcione, seu projeto deve ter um formulário denominado `SidebarMenu`.</span><span class="sxs-lookup"><span data-stu-id="1728f-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>  
  
 <span data-ttu-id="1728f-134">Esse código funcionará somente em um projeto de aplicativo do Windows.</span><span class="sxs-lookup"><span data-stu-id="1728f-134">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1728f-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1728f-135">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="1728f-136">Disponibilidade por tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="1728f-136">Availability by Project Type</span></span>  
  
|<span data-ttu-id="1728f-137">Tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="1728f-137">Project type</span></span>|<span data-ttu-id="1728f-138">Disponível</span><span class="sxs-lookup"><span data-stu-id="1728f-138">Available</span></span>|  
|---|---|  
|<span data-ttu-id="1728f-139">Aplicativo do Windows</span><span class="sxs-lookup"><span data-stu-id="1728f-139">Windows Application</span></span>|<span data-ttu-id="1728f-140">**Sim**</span><span class="sxs-lookup"><span data-stu-id="1728f-140">**Yes**</span></span>|  
|<span data-ttu-id="1728f-141">Biblioteca de Classes</span><span class="sxs-lookup"><span data-stu-id="1728f-141">Class Library</span></span>|<span data-ttu-id="1728f-142">Não</span><span class="sxs-lookup"><span data-stu-id="1728f-142">No</span></span>|  
|<span data-ttu-id="1728f-143">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="1728f-143">Console Application</span></span>|<span data-ttu-id="1728f-144">Não</span><span class="sxs-lookup"><span data-stu-id="1728f-144">No</span></span>|  
|<span data-ttu-id="1728f-145">Biblioteca de controle do Windows</span><span class="sxs-lookup"><span data-stu-id="1728f-145">Windows Control Library</span></span>|<span data-ttu-id="1728f-146">Não</span><span class="sxs-lookup"><span data-stu-id="1728f-146">No</span></span>|  
|<span data-ttu-id="1728f-147">Biblioteca de controle da Web</span><span class="sxs-lookup"><span data-stu-id="1728f-147">Web Control Library</span></span>|<span data-ttu-id="1728f-148">Não</span><span class="sxs-lookup"><span data-stu-id="1728f-148">No</span></span>|  
|<span data-ttu-id="1728f-149">Serviço do Windows</span><span class="sxs-lookup"><span data-stu-id="1728f-149">Windows Service</span></span>|<span data-ttu-id="1728f-150">Não</span><span class="sxs-lookup"><span data-stu-id="1728f-150">No</span></span>|  
|<span data-ttu-id="1728f-151">Site da Web</span><span class="sxs-lookup"><span data-stu-id="1728f-151">Web Site</span></span>|<span data-ttu-id="1728f-152">Não</span><span class="sxs-lookup"><span data-stu-id="1728f-152">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1728f-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1728f-153">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [<span data-ttu-id="1728f-154">Objetos</span><span class="sxs-lookup"><span data-stu-id="1728f-154">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)  
 [<span data-ttu-id="1728f-155">Operador Is</span><span class="sxs-lookup"><span data-stu-id="1728f-155">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="1728f-156">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="1728f-156">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="1728f-157">Acessando formulários de aplicativo</span><span class="sxs-lookup"><span data-stu-id="1728f-157">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
