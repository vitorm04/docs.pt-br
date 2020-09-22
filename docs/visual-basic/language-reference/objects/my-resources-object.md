---
title: Objeto My.Resources
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: 3d12524706f680434d5b6d8da39c89042bea3281
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867332"
---
# <a name="myresources-object"></a><span data-ttu-id="906b3-102">Objeto My.Resources</span><span class="sxs-lookup"><span data-stu-id="906b3-102">My.Resources Object</span></span>

<span data-ttu-id="906b3-103">Fornece propriedades e classes para acessar os recursos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="906b3-103">Provides properties and classes for accessing the application's resources.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="906b3-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="906b3-104">Remarks</span></span>  

 <span data-ttu-id="906b3-105">O `My.Resources` objeto fornece acesso aos recursos do aplicativo e permite que você recupere dinamicamente os recursos para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="906b3-105">The `My.Resources` object provides access to the application's resources and lets you dynamically retrieve resources for your application.</span></span> <span data-ttu-id="906b3-106">Para obter mais informações, consulte [Gerenciando recursos de aplicativos (.net)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="906b3-106">For more information, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
 <span data-ttu-id="906b3-107">O `My.Resources` objeto expõe apenas recursos globais.</span><span class="sxs-lookup"><span data-stu-id="906b3-107">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="906b3-108">Ele não fornece acesso aos arquivos de recursos associados aos formulários.</span><span class="sxs-lookup"><span data-stu-id="906b3-108">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="906b3-109">Você deve acessar os recursos do formulário no formulário.</span><span class="sxs-lookup"><span data-stu-id="906b3-109">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="906b3-110">Você pode acessar os arquivos de recursos específicos da cultura do aplicativo a partir do `My.Resources` objeto.</span><span class="sxs-lookup"><span data-stu-id="906b3-110">You can access the application's culture-specific resource files from the `My.Resources` object.</span></span> <span data-ttu-id="906b3-111">Por padrão, o `My.Resources` objeto pesquisa os recursos do arquivo de recursos que corresponde à cultura na <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="906b3-111">By default, the `My.Resources` object looks up resources from the resource file that matches the culture in the <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> property.</span></span> <span data-ttu-id="906b3-112">No entanto, você pode substituir esse comportamento e especificar uma cultura específica a ser usada para os recursos.</span><span class="sxs-lookup"><span data-stu-id="906b3-112">However, you can override this behavior and specify a particular culture to use for the resources.</span></span> <span data-ttu-id="906b3-113">Para saber mais, veja [Recursos em aplicativos da área de trabalho](../../../framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="906b3-113">For more information, see [Resources in Desktop Apps](../../../framework/resources/index.md).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="906b3-114">Propriedades</span><span class="sxs-lookup"><span data-stu-id="906b3-114">Properties</span></span>  

 <span data-ttu-id="906b3-115">As propriedades do `My.Resources` objeto fornecem acesso somente leitura aos recursos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="906b3-115">The properties of the `My.Resources` object provide read-only access to your application's resources.</span></span> <span data-ttu-id="906b3-116">Para adicionar ou remover recursos, use o **Designer de projeto**.</span><span class="sxs-lookup"><span data-stu-id="906b3-116">To add or remove resources, use the **Project Designer**.</span></span> <span data-ttu-id="906b3-117">Você pode acessar os recursos adicionados por meio do **Designer de projeto** usando `My.Resources.` *resourceName*.</span><span class="sxs-lookup"><span data-stu-id="906b3-117">You can access resources added through the **Project Designer** by using `My.Resources.`*resourceName*.</span></span>  
  
 <span data-ttu-id="906b3-118">Você também pode adicionar ou remover arquivos de recursos selecionando seu projeto no **Gerenciador de soluções** e clicando em **Adicionar novo item** ou **Adicionar item existente** no menu **projeto** .</span><span class="sxs-lookup"><span data-stu-id="906b3-118">You can also add or remove resource files by selecting your project in **Solution Explorer** and clicking **Add New Item** or **Add Existing Item** from the **Project** menu.</span></span> <span data-ttu-id="906b3-119">Você pode acessar recursos adicionados dessa maneira usando `My.Resources.` *resourceFileName* `.` *resourceName*.</span><span class="sxs-lookup"><span data-stu-id="906b3-119">You can access resources added in this manner by using `My.Resources.`*resourceFileName*`.`*resourceName*.</span></span>  
  
 <span data-ttu-id="906b3-120">Cada recurso tem um nome, categoria e valor, e essas configurações de recurso determinam como a propriedade para acessar o recurso aparece no `My.Resources` objeto.</span><span class="sxs-lookup"><span data-stu-id="906b3-120">Each resource has a name, category, and value, and these resource settings determine how the property to access the resource appears in the `My.Resources` object.</span></span> <span data-ttu-id="906b3-121">Para recursos adicionados no **Designer de projeto**:</span><span class="sxs-lookup"><span data-stu-id="906b3-121">For resources added in the **Project Designer**:</span></span>  
  
- <span data-ttu-id="906b3-122">O nome determina o nome da propriedade,</span><span class="sxs-lookup"><span data-stu-id="906b3-122">The name determines the name of the property,</span></span>  
  
- <span data-ttu-id="906b3-123">Os dados de recurso são o valor da propriedade,</span><span class="sxs-lookup"><span data-stu-id="906b3-123">The resource data is the value of the property,</span></span>  
  
- <span data-ttu-id="906b3-124">A categoria determina o tipo da propriedade:</span><span class="sxs-lookup"><span data-stu-id="906b3-124">The category determines the type of the property:</span></span>  
  
|<span data-ttu-id="906b3-125">Categoria</span><span class="sxs-lookup"><span data-stu-id="906b3-125">Category</span></span>|<span data-ttu-id="906b3-126">Tipo de dados de propriedade</span><span class="sxs-lookup"><span data-stu-id="906b3-126">Property data type</span></span>|  
|---|---|  
|<span data-ttu-id="906b3-127">**Cadeias de caracteres**</span><span class="sxs-lookup"><span data-stu-id="906b3-127">**Strings**</span></span>|[<span data-ttu-id="906b3-128">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="906b3-128">String</span></span>](../data-types/string-data-type.md)|  
|<span data-ttu-id="906b3-129">**Imagens**</span><span class="sxs-lookup"><span data-stu-id="906b3-129">**Images**</span></span>|<xref:System.Drawing.Bitmap>|  
|<span data-ttu-id="906b3-130">**Ícones**</span><span class="sxs-lookup"><span data-stu-id="906b3-130">**Icons**</span></span>|<xref:System.Drawing.Icon>|  
|<span data-ttu-id="906b3-131">**Áudio**</span><span class="sxs-lookup"><span data-stu-id="906b3-131">**Audio**</span></span>|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <span data-ttu-id="906b3-132">A <xref:System.IO.UnmanagedMemoryStream> classe deriva da <xref:System.IO.Stream> classe, portanto, ela pode ser usada com métodos que usam fluxos, como o <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> método.</span><span class="sxs-lookup"><span data-stu-id="906b3-132">The <xref:System.IO.UnmanagedMemoryStream> class derives from the <xref:System.IO.Stream> class, so it can be used with methods that take streams, such as the <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> method.</span></span>|  
|<span data-ttu-id="906b3-133">**Arquivos**</span><span class="sxs-lookup"><span data-stu-id="906b3-133">**Files**</span></span>|<span data-ttu-id="906b3-134">-   [Cadeia de caracteres](../data-types/string-data-type.md) para arquivos de texto.</span><span class="sxs-lookup"><span data-stu-id="906b3-134">-   [String](../data-types/string-data-type.md) for text files.</span></span><br /><span data-ttu-id="906b3-135">-   <xref:System.Drawing.Bitmap> para arquivos de imagem.</span><span class="sxs-lookup"><span data-stu-id="906b3-135">-   <xref:System.Drawing.Bitmap> for image files.</span></span><br /><span data-ttu-id="906b3-136">-   <xref:System.Drawing.Icon> para arquivos de ícone.</span><span class="sxs-lookup"><span data-stu-id="906b3-136">-   <xref:System.Drawing.Icon> for icon files.</span></span><br /><span data-ttu-id="906b3-137">-   <xref:System.IO.UnmanagedMemoryStream> para arquivos de som.</span><span class="sxs-lookup"><span data-stu-id="906b3-137">-   <xref:System.IO.UnmanagedMemoryStream> for sound files.</span></span>|  
|<span data-ttu-id="906b3-138">**Outras**</span><span class="sxs-lookup"><span data-stu-id="906b3-138">**Other**</span></span>|<span data-ttu-id="906b3-139">Determinado pelas informações na coluna **Type** do designer.</span><span class="sxs-lookup"><span data-stu-id="906b3-139">Determined by the information in the designer's **Type** column.</span></span>|  
  
## <a name="classes"></a><span data-ttu-id="906b3-140">Classes</span><span class="sxs-lookup"><span data-stu-id="906b3-140">Classes</span></span>  

 <span data-ttu-id="906b3-141">O `My.Resources` objeto expõe cada arquivo de recurso como uma classe com propriedades compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="906b3-141">The `My.Resources` object exposes each resource file as a class with shared properties.</span></span> <span data-ttu-id="906b3-142">O nome da classe é o mesmo que o nome do arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="906b3-142">The class name is the same as the name of the resource file.</span></span> <span data-ttu-id="906b3-143">Conforme descrito na seção anterior, os recursos em um arquivo de recurso são expostos como propriedades na classe.</span><span class="sxs-lookup"><span data-stu-id="906b3-143">As described in the previous section, the resources in a resource file are exposed as properties in the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="906b3-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="906b3-144">Example</span></span>  

 <span data-ttu-id="906b3-145">Este exemplo define o título de um formulário para o recurso de cadeia de caracteres chamado `Form1Title` no arquivo de recurso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="906b3-145">This example sets the title of a form to the string resource named `Form1Title` in the application resource file.</span></span> <span data-ttu-id="906b3-146">Para que o exemplo funcione, o aplicativo deve ter uma cadeia de caracteres chamada `Form1Title` em seu arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="906b3-146">For the example to work, the application must have a string named `Form1Title` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="906b3-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="906b3-147">Example</span></span>  

 <span data-ttu-id="906b3-148">Este exemplo define o ícone do formulário para o ícone chamado `Form1Icon` que é armazenado no arquivo de recurso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="906b3-148">This example sets the icon of the form to the icon named `Form1Icon` that is stored in the application's resource file.</span></span> <span data-ttu-id="906b3-149">Para que o exemplo funcione, o aplicativo deve ter um ícone chamado `Form1Icon` em seu arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="906b3-149">For the example to work, the application must have an icon named `Form1Icon` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="906b3-150">Exemplo</span><span class="sxs-lookup"><span data-stu-id="906b3-150">Example</span></span>  

 <span data-ttu-id="906b3-151">Este exemplo define a imagem de plano de fundo de um formulário para o recurso de imagem chamado `Form1Background` , que está no arquivo de recurso de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="906b3-151">This example sets the background image of a form to the image resource named `Form1Background`, which is in the application resource file.</span></span> <span data-ttu-id="906b3-152">Para que este exemplo funcione, o aplicativo deve ter um recurso de imagem chamado `Form1Background` em seu arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="906b3-152">For this example to work, the application must have an image resource named `Form1Background` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="906b3-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="906b3-153">Example</span></span>  

 <span data-ttu-id="906b3-154">Este exemplo reproduz o som que é armazenado como um recurso de áudio chamado `Form1Greeting` no arquivo de recurso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="906b3-154">This example plays the sound that is stored as an audio resource named `Form1Greeting` in the application's resource file.</span></span> <span data-ttu-id="906b3-155">Para que o exemplo funcione, o aplicativo deve ter um recurso de áudio chamado `Form1Greeting` em seu arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="906b3-155">For the example to work, the application must have an audio resource named `Form1Greeting` in its resource file.</span></span> <span data-ttu-id="906b3-156">O `My.Computer.Audio.Play` método está disponível somente para aplicativos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="906b3-156">The `My.Computer.Audio.Play` method is available only for Windows Forms applications.</span></span>  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="906b3-157">Exemplo</span><span class="sxs-lookup"><span data-stu-id="906b3-157">Example</span></span>  

 <span data-ttu-id="906b3-158">Este exemplo recupera a versão de cultura francesa de um recurso de cadeia de caracteres do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="906b3-158">This example retrieves the French-culture version of a  string resource of the application.</span></span> <span data-ttu-id="906b3-159">O recurso é nomeado `Message` .</span><span class="sxs-lookup"><span data-stu-id="906b3-159">The resource is named `Message`.</span></span> <span data-ttu-id="906b3-160">Para alterar a cultura usada pelo `My.Resources` objeto, o exemplo usa <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A> .</span><span class="sxs-lookup"><span data-stu-id="906b3-160">To change the culture that the `My.Resources` object uses, the example uses <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</span></span>  
  
 <span data-ttu-id="906b3-161">Para que este exemplo funcione, o aplicativo deve ter uma cadeia de caracteres chamada `Message` em seu arquivo de recurso e o aplicativo deve ter a versão de cultura francesa desse arquivo de recurso, Resources.fr-fr. resx.</span><span class="sxs-lookup"><span data-stu-id="906b3-161">For this example to work, the application must have a string named `Message` in its resource file, and the application should have the French-culture version of that resource file, Resources.fr-FR.resx.</span></span> <span data-ttu-id="906b3-162">Se o aplicativo não tiver a versão de cultura francesa do arquivo de recurso, o `My.Resource` objeto recuperará o recurso do arquivo de recurso de cultura padrão.</span><span class="sxs-lookup"><span data-stu-id="906b3-162">If the application does not have the French-culture version of the resource file, the `My.Resource` object retrieves the resource from the default-culture resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="906b3-163">Confira também</span><span class="sxs-lookup"><span data-stu-id="906b3-163">See also</span></span>

- [<span data-ttu-id="906b3-164">Gerenciando recursos de aplicativo (.NET)</span><span class="sxs-lookup"><span data-stu-id="906b3-164">Managing Application Resources (.NET)</span></span>](/visualstudio/ide/managing-application-resources-dotnet)
- [<span data-ttu-id="906b3-165">Recursos em aplicativos de área de trabalho</span><span class="sxs-lookup"><span data-stu-id="906b3-165">Resources in Desktop Apps</span></span>](../../../framework/resources/index.md)
