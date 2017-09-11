---
title: /link (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
caps.latest.revision: 27
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
ms.openlocfilehash: 71ecefc898ca37cbf7299d97518e1ce2547a58da
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="link-visual-basic"></a><span data-ttu-id="bfd52-102">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfd52-102">/link (Visual Basic)</span></span>
<span data-ttu-id="bfd52-103">Faz com que o compilador disponibilizar informações de tipo COM nos assemblies especificados para o projeto que você está compilando atualmente.</span><span class="sxs-lookup"><span data-stu-id="bfd52-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfd52-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfd52-104">Syntax</span></span>  
  
```  
/link:fileList  
' -or-  
/l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="bfd52-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bfd52-105">Arguments</span></span>  
  
|<span data-ttu-id="bfd52-106">Termo</span><span class="sxs-lookup"><span data-stu-id="bfd52-106">Term</span></span>|<span data-ttu-id="bfd52-107">Definição</span><span class="sxs-lookup"><span data-stu-id="bfd52-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="bfd52-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="bfd52-108">Required.</span></span> <span data-ttu-id="bfd52-109">Lista delimitada por vírgulas de nomes de arquivo de assembly.</span><span class="sxs-lookup"><span data-stu-id="bfd52-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="bfd52-110">Se o nome do arquivo contém um espaço, coloque o nome entre aspas.</span><span class="sxs-lookup"><span data-stu-id="bfd52-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfd52-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="bfd52-111">Remarks</span></span>  
 <span data-ttu-id="bfd52-112">O `/link` opção permite que você implantar um aplicativo que incorporou informações de tipo.</span><span class="sxs-lookup"><span data-stu-id="bfd52-112">The `/link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="bfd52-113">O aplicativo pode usar tipos em um assembly de tempo de execução que implementam as informações de tipo inserido sem a necessidade de uma referência ao assembly de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bfd52-113">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="bfd52-114">Se várias versões do assembly em tempo de execução são publicadas, o aplicativo que contém as informações de tipo inserido pode trabalhar com várias versões sem precisar ser recompilado.</span><span class="sxs-lookup"><span data-stu-id="bfd52-114">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="bfd52-115">Para obter um exemplo, consulte [passo a passo: inserindo tipos de Assemblies gerenciados](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span><span class="sxs-lookup"><span data-stu-id="bfd52-115">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="bfd52-116">Usando o `/link` opção é especialmente útil quando você está trabalhando com interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="bfd52-116">Using the `/link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="bfd52-117">Você pode inserir tipos COM para que seu aplicativo não exige um assembly de interoperabilidade primária (PIA) no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="bfd52-117">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="bfd52-118">O `/link` opção instrui o compilador a inserir as informações de tipo de COM do assembly referenciado interoperabilidade no código compilado resultante.</span><span class="sxs-lookup"><span data-stu-id="bfd52-118">The `/link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="bfd52-119">O tipo COM é identificado pelo valor CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="bfd52-119">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="bfd52-120">Como resultado, o aplicativo pode ser executado em um computador de destino que tenha instalado os mesmos tipos COM os mesmos valores CLSID.</span><span class="sxs-lookup"><span data-stu-id="bfd52-120">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="bfd52-121">Os aplicativos que automatizam o Microsoft Office são um bom exemplo.</span><span class="sxs-lookup"><span data-stu-id="bfd52-121">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="bfd52-122">Como aplicativos como o Office normalmente mantêm o mesmo valor CLSID entre diferentes versões, seu aplicativo pode usar tipos referenciados COM longa como .NET Framework 4 ou posterior estiver instalada no computador de destino e seu aplicativo usa métodos, propriedades ou eventos que estão incluídos nos tipos referenciados COM.</span><span class="sxs-lookup"><span data-stu-id="bfd52-122">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="bfd52-123">O `/link` opção incorpora apenas interfaces, estruturas e delegados.</span><span class="sxs-lookup"><span data-stu-id="bfd52-123">The `/link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="bfd52-124">Não há suporte para a incorporação de classes COM.</span><span class="sxs-lookup"><span data-stu-id="bfd52-124">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfd52-125">Quando você cria uma instância de um tipo COM inserido no seu código, você deve criar a instância usando a interface apropriada.</span><span class="sxs-lookup"><span data-stu-id="bfd52-125">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="bfd52-126">Tentativa de criar uma instância de um tipo COM inserido usando o CoClass causa um erro.</span><span class="sxs-lookup"><span data-stu-id="bfd52-126">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="bfd52-127">Para definir o `/link` opção [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], adicione uma referência de assembly e defina o `Embed Interop Types` propriedade **true**.</span><span class="sxs-lookup"><span data-stu-id="bfd52-127">To set the `/link` option in [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="bfd52-128">O padrão para o `Embed Interop Types` é de propriedade **false**.</span><span class="sxs-lookup"><span data-stu-id="bfd52-128">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="bfd52-129">Se você vincular a um assembly COM (Assembly A) que se faz referência a outro assembly COM (Assembly B), você também precisa vincular ao Assembly B se uma das seguintes opções for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="bfd52-129">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="bfd52-130">Um tipo do Assembly A herda de um tipo ou implementa uma interface do Assembly B.</span><span class="sxs-lookup"><span data-stu-id="bfd52-130">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="bfd52-131">Um campo, propriedade, evento ou método que possui um tipo de parâmetro ou tipo de retorno do Assembly B é chamado.</span><span class="sxs-lookup"><span data-stu-id="bfd52-131">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="bfd52-132">Use [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) para especificar o diretório no qual uma ou mais das suas referências do assembly estão localizado.</span><span class="sxs-lookup"><span data-stu-id="bfd52-132">Use [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="bfd52-133">Como o [/Reference](../../../visual-basic/reference/command-line-compiler/reference.md) opção de compilador, o `/link` opção de compilador usa o arquivo de resposta Vbc, que frequentemente usadas referências [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies.</span><span class="sxs-lookup"><span data-stu-id="bfd52-133">Like the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) compiler option, the `/link` compiler option uses the Vbc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies.</span></span> <span data-ttu-id="bfd52-134">Use o [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) opção de compilador se não quiser que o compilador para usar o arquivo Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="bfd52-134">Use the [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="bfd52-135">A forma abreviada do `/link` é `/l`.</span><span class="sxs-lookup"><span data-stu-id="bfd52-135">The short form of `/link` is `/l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="bfd52-136">Genéricos e tipos inseridos</span><span class="sxs-lookup"><span data-stu-id="bfd52-136">Generics and Embedded Types</span></span>  
 <span data-ttu-id="bfd52-137">As seções a seguir descrevem as limitações no uso de tipos genéricos em aplicativos que inserir tipos de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="bfd52-137">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="bfd52-138">Interfaces genéricas</span><span class="sxs-lookup"><span data-stu-id="bfd52-138">Generic Interfaces</span></span>  
 <span data-ttu-id="bfd52-139">Interfaces genéricas que são inseridos de um assembly de interoperabilidade não podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="bfd52-139">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="bfd52-140">Isso é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="bfd52-140">This is shown in the following example.</span></span>  
  
 <span data-ttu-id="bfd52-141">[!code-vb[VbLinkCompiler n º&1;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="bfd52-141">[!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]</span></span>  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="bfd52-142">Tipos que têm parâmetros genéricos</span><span class="sxs-lookup"><span data-stu-id="bfd52-142">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="bfd52-143">Tipos que têm um parâmetro genérico cujo tipo é incorporado a partir de um assembly de interoperabilidade não podem ser usados se for do tipo de um assembly externo.</span><span class="sxs-lookup"><span data-stu-id="bfd52-143">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="bfd52-144">Essa restrição não se aplicam a interfaces.</span><span class="sxs-lookup"><span data-stu-id="bfd52-144">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="bfd52-145">Por exemplo, considere o <xref:Microsoft.Office.Interop.Excel.Range>interface é definida no <xref:Microsoft.Office.Interop.Excel>assembly.</xref:Microsoft.Office.Interop.Excel> </xref:Microsoft.Office.Interop.Excel.Range></span><span class="sxs-lookup"><span data-stu-id="bfd52-145">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="bfd52-146">Se uma biblioteca incorpora tipos de interoperabilidade do <xref:Microsoft.Office.Interop.Excel>assembly e expõe um método que retorna um tipo genérico que tem um parâmetro cujo tipo é o <xref:Microsoft.Office.Interop.Excel.Range>da interface, que o método deve retornar uma interface genérica, conforme mostrado no exemplo de código a seguir.</xref:Microsoft.Office.Interop.Excel.Range> </xref:Microsoft.Office.Interop.Excel></span><span class="sxs-lookup"><span data-stu-id="bfd52-146">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 <span data-ttu-id="bfd52-147">[!code-vb[VbLinkCompiler n º&2;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="bfd52-147">[!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]</span></span>  
<span data-ttu-id="bfd52-148">[!code-vb[VbLinkCompiler n º&3;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="bfd52-148">[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]</span></span>  
<span data-ttu-id="bfd52-149">[!code-vb[VbLinkCompiler n º&4;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="bfd52-149">[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]</span></span>  
  
 <span data-ttu-id="bfd52-150">No exemplo a seguir, o código do cliente pode chamar o método que retorna o <xref:System.Collections.IList>interface genérica sem erro.</xref:System.Collections.IList></span><span class="sxs-lookup"><span data-stu-id="bfd52-150">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 <span data-ttu-id="bfd52-151">[!code-vb[VbLinkCompiler n º&5;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="bfd52-151">[!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfd52-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bfd52-152">Example</span></span>  
 <span data-ttu-id="bfd52-153">O código a seguir compila o arquivo de origem `OfficeApp.vb` e fazer referência a assemblies de `COMData1.dll` e `COMData2.dll` para produzir `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="bfd52-153">The following code compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```vb  
vbc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bfd52-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfd52-154">See Also</span></span>  
 <span data-ttu-id="bfd52-155">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="bfd52-155">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="bfd52-156"> [Passo a passo: Inserindo tipos de Assemblies gerenciados](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21) </span><span class="sxs-lookup"><span data-stu-id="bfd52-156"> [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21) </span></span>  
<span data-ttu-id="bfd52-157"> [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span><span class="sxs-lookup"><span data-stu-id="bfd52-157"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span></span>  
<span data-ttu-id="bfd52-158"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span><span class="sxs-lookup"><span data-stu-id="bfd52-158"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span></span>  
<span data-ttu-id="bfd52-159"> [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) </span><span class="sxs-lookup"><span data-stu-id="bfd52-159"> [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) </span></span>  
<span data-ttu-id="bfd52-160"> [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="bfd52-160"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="bfd52-161"> [Introdução à Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)</span><span class="sxs-lookup"><span data-stu-id="bfd52-161"> [Introduction to COM Interop](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)</span></span>
