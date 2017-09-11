---
title: Objeto My. Forms | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Forms
- My.MyProject.Forms
dev_langs:
- VB
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e15adcad0714c4ef0a9c1d0b5e63a18d9d0c1dcc
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="myforms-object"></a><span data-ttu-id="f6cf4-102">Objeto My.Forms</span><span class="sxs-lookup"><span data-stu-id="f6cf4-102">My.Forms Object</span></span>
<span data-ttu-id="f6cf4-103">Fornece propriedades para acessar uma instância de cada Windows form declarado no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6cf4-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="f6cf4-104">Remarks</span></span>  
 <span data-ttu-id="f6cf4-105">O `My.Forms` objeto fornece uma instância de cada formulário no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="f6cf4-106">O nome da propriedade é igual ao nome do formulário que acessa a propriedade.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-106">The name of the property is the same as the name of the form that the property accesses.</span></span> <span data-ttu-id="f6cf4-107">Para obter informações sobre como adicionar formas a um projeto, consulte [como: adicionar formulários do Windows para um projeto](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="f6cf4-107">For information about adding forms to a project, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="f6cf4-108">Você pode acessar os formulários fornecidos pelo `My.Forms` objeto usando o nome do formulário, sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-108">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="f6cf4-109">Como o nome da propriedade é o mesmo nome do tipo do formulário, isso permite que você acesse um formulário como se tivesse uma instância padrão.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-109">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="f6cf4-110">Por exemplo, `My.Forms.Form1.Show` é equivalente a `Form1.Show`.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-110">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="f6cf4-111">O `My.Forms` objeto expõe apenas as formas associadas ao projeto atual.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-111">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="f6cf4-112">Ele não fornece acesso aos formulários declarado em DLLs referenciados.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-112">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="f6cf4-113">Para acessar um formulário que fornece uma DLL, você deve usar o nome qualificado do formulário, gravado como *DllName*.* Nome do formulário*.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-113">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="f6cf4-114">Você pode usar o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>propriedade para obter uma coleção de todos os formulários do aplicativo aberto.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A></span><span class="sxs-lookup"><span data-stu-id="f6cf4-114">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="f6cf4-115">O objeto e suas propriedades estão disponíveis apenas para aplicativos do Windows.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-115">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f6cf4-116">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f6cf4-116">Properties</span></span>  
 <span data-ttu-id="f6cf4-117">Cada propriedade do `My.Forms` objeto fornece acesso a uma instância de um formulário no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-117">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="f6cf4-118">O nome da propriedade é igual ao nome do formulário que acessa a propriedade e o tipo de propriedade é o mesmo tipo do formulário.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-118">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6cf4-119">Se houver uma colisão de nomes, o nome da propriedade para acessar um formulário é *RootNamespace*_*Namespace*\_*nome do formulário*.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-119">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="f6cf4-120">Por exemplo, considere dois formulários denominados `Form1.`se uma dessas formas está no namespace raiz `WindowsApplication1` e no namespace `Namespace1`, você acessaria o formulário por meio de `My.Forms.WindowsApplication1_Namespace1_Form1`.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-120">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="f6cf4-121">O `My.Forms` objeto fornece acesso à instância do formulário principal do aplicativo que foi criada na inicialização.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-121">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="f6cf4-122">Para todas as outras formas, o `My.Forms` objeto cria uma nova instância do formulário quando ele é acessado e armazena.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-122">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="f6cf4-123">Tentativas subsequentes para acessar essa propriedade retornam essa instância do formulário.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-123">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="f6cf4-124">Você pode descartar um formulário atribuindo `Nothing` para a propriedade desse formulário.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-124">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="f6cf4-125">A propriedade setter chama o <xref:System.Windows.Forms.Form.Close%2A>método do formulário e, em seguida, atribui `Nothing` para o valor armazenado.</xref:System.Windows.Forms.Form.Close%2A></span><span class="sxs-lookup"><span data-stu-id="f6cf4-125">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="f6cf4-126">Se você atribuir qualquer valor diferente de `Nothing` à propriedade setter lança um <xref:System.ArgumentException>exceção.</xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="f6cf4-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="f6cf4-127">Você pode testar se uma propriedade do `My.Forms` objeto armazena uma instância do formulário usando o `Is` ou `IsNot` operador.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-127">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="f6cf4-128">Você pode usar os operadores para verificar se o valor da propriedade é `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6cf4-129">Normalmente, o `Is` ou `IsNot` operador precisa ler o valor da propriedade para executar a comparação.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="f6cf4-130">No entanto, se a propriedade armazena atualmente `Nothing`, a propriedade cria uma nova instância do formulário e, em seguida, retorna essa instância.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-130">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="f6cf4-131">No entanto, o compilador Visual Basic trata as propriedades do `My.Forms` diferente do objeto e permite que o `Is` ou `IsNot` operador para verificar o status da propriedade sem alterar seu valor.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-131">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6cf4-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6cf4-132">Example</span></span>  
 <span data-ttu-id="f6cf4-133">Este exemplo altera o título do padrão `SidebarMenu` formulário.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-133">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 <span data-ttu-id="f6cf4-134">[!code-vb[VbVbalrMyForms n º&2;](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f6cf4-134">[!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]</span></span>  
  
 <span data-ttu-id="f6cf4-135">Para esse exemplo funcione, seu projeto deve ter um formulário chamado `SidebarMenu`.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-135">For this example to work, your project must have a form named `SidebarMenu`.</span></span> <span data-ttu-id="f6cf4-136">Para obter mais informações, consulte [como: adicionar formulários do Windows para um projeto](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="f6cf4-136">For more information, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="f6cf4-137">Esse código funciona apenas em um projeto de aplicativo do Windows.</span><span class="sxs-lookup"><span data-stu-id="f6cf4-137">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6cf4-138">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6cf4-138">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="f6cf4-139">Disponibilidade por tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="f6cf4-139">Availability by Project Type</span></span>  
  
|<span data-ttu-id="f6cf4-140">Tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="f6cf4-140">Project type</span></span>|<span data-ttu-id="f6cf4-141">Disponível</span><span class="sxs-lookup"><span data-stu-id="f6cf4-141">Available</span></span>|  
|---|---|  
|<span data-ttu-id="f6cf4-142">Aplicativo do Windows</span><span class="sxs-lookup"><span data-stu-id="f6cf4-142">Windows Application</span></span>|<span data-ttu-id="f6cf4-143">**Sim**</span><span class="sxs-lookup"><span data-stu-id="f6cf4-143">**Yes**</span></span>|  
|<span data-ttu-id="f6cf4-144">Biblioteca de Classes</span><span class="sxs-lookup"><span data-stu-id="f6cf4-144">Class Library</span></span>|<span data-ttu-id="f6cf4-145">Não</span><span class="sxs-lookup"><span data-stu-id="f6cf4-145">No</span></span>|  
|<span data-ttu-id="f6cf4-146">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="f6cf4-146">Console Application</span></span>|<span data-ttu-id="f6cf4-147">Não</span><span class="sxs-lookup"><span data-stu-id="f6cf4-147">No</span></span>|  
|<span data-ttu-id="f6cf4-148">Biblioteca de controle do Windows</span><span class="sxs-lookup"><span data-stu-id="f6cf4-148">Windows Control Library</span></span>|<span data-ttu-id="f6cf4-149">Não</span><span class="sxs-lookup"><span data-stu-id="f6cf4-149">No</span></span>|  
|<span data-ttu-id="f6cf4-150">Biblioteca de Controles da Web</span><span class="sxs-lookup"><span data-stu-id="f6cf4-150">Web Control Library</span></span>|<span data-ttu-id="f6cf4-151">Não</span><span class="sxs-lookup"><span data-stu-id="f6cf4-151">No</span></span>|  
|<span data-ttu-id="f6cf4-152">Serviço do Windows</span><span class="sxs-lookup"><span data-stu-id="f6cf4-152">Windows Service</span></span>|<span data-ttu-id="f6cf4-153">Não</span><span class="sxs-lookup"><span data-stu-id="f6cf4-153">No</span></span>|  
|<span data-ttu-id="f6cf4-154">Site</span><span class="sxs-lookup"><span data-stu-id="f6cf4-154">Web Site</span></span>|<span data-ttu-id="f6cf4-155">Não</span><span class="sxs-lookup"><span data-stu-id="f6cf4-155">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6cf4-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6cf4-156">See Also</span></span>  
 <span data-ttu-id="f6cf4-157"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A></span><span class="sxs-lookup"><span data-stu-id="f6cf4-157"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A></span></span>   
 <span data-ttu-id="f6cf4-158"><xref:System.Windows.Forms.Form></xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="f6cf4-158"><xref:System.Windows.Forms.Form></span></span>   
 <span data-ttu-id="f6cf4-159"><xref:System.Windows.Forms.Form.Close%2A></xref:System.Windows.Forms.Form.Close%2A></span><span class="sxs-lookup"><span data-stu-id="f6cf4-159"><xref:System.Windows.Forms.Form.Close%2A></span></span>   
<span data-ttu-id="f6cf4-160"> [Objetos](../../../visual-basic/language-reference/objects/index.md) </span><span class="sxs-lookup"><span data-stu-id="f6cf4-160"> [Objects](../../../visual-basic/language-reference/objects/index.md) </span></span>  
<span data-ttu-id="f6cf4-161"> [Como: adicionar formulários do Windows a um projeto](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1) </span><span class="sxs-lookup"><span data-stu-id="f6cf4-161"> [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1) </span></span>  
<span data-ttu-id="f6cf4-162"> [Operador is](../../../visual-basic/language-reference/operators/is-operator.md) </span><span class="sxs-lookup"><span data-stu-id="f6cf4-162"> [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md) </span></span>  
<span data-ttu-id="f6cf4-163"> [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md) </span><span class="sxs-lookup"><span data-stu-id="f6cf4-163"> [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md) </span></span>  
<span data-ttu-id="f6cf4-164"> [Acessando formulários de aplicativo](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)</span><span class="sxs-lookup"><span data-stu-id="f6cf4-164"> [Accessing Application Forms](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)</span></span>
