---
title: -link (Visual Basic)
ms.date: 03/10/2018
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
ms.openlocfilehash: 91eba53eb8094e55af09d406515dad16fc71937d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536811"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="b8750-102">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8750-102">-link (Visual Basic)</span></span>
<span data-ttu-id="b8750-103">Faz com que o compilador disponibilize as informações de tipo COM nos assemblies especificados para o projeto sendo compilado no momento.</span><span class="sxs-lookup"><span data-stu-id="b8750-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8750-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8750-104">Syntax</span></span>  
  
```  
-link:fileList  
' -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="b8750-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b8750-105">Arguments</span></span>  
  
|<span data-ttu-id="b8750-106">Termo</span><span class="sxs-lookup"><span data-stu-id="b8750-106">Term</span></span>|<span data-ttu-id="b8750-107">Definição</span><span class="sxs-lookup"><span data-stu-id="b8750-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="b8750-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b8750-108">Required.</span></span> <span data-ttu-id="b8750-109">Lista delimitada por vírgulas de nomes de arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="b8750-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="b8750-110">Se o nome do arquivo contém um espaço, coloque o nome entre aspas.</span><span class="sxs-lookup"><span data-stu-id="b8750-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8750-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8750-111">Remarks</span></span>  
 <span data-ttu-id="b8750-112">A opção `-link` permite que você implante um aplicativo que inseriu informações de tipo.</span><span class="sxs-lookup"><span data-stu-id="b8750-112">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="b8750-113">O aplicativo pode usar tipos em um assembly de tempo de execução que implementa as informações de tipo inseridas sem a necessidade de uma referência ao assembly de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b8750-113">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="b8750-114">Se forem publicadas várias versões do assembly de tempo de execução, o aplicativo que contém as informações de tipo inseridas poderá trabalhar com as várias versões sem precisar ser recompilado.</span><span class="sxs-lookup"><span data-stu-id="b8750-114">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="b8750-115">Para obter um exemplo, consulte [Instruções passo a passo: Inserindo tipos de assemblies gerenciado](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span><span class="sxs-lookup"><span data-stu-id="b8750-115">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="b8750-116">Usar a opção `-link` é especialmente útil quando você está trabalhando com a interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="b8750-116">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="b8750-117">Você pode inserir tipos COM para que seu aplicativo não precise mais de um PIA (assembly de interoperabilidade primário) no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="b8750-117">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="b8750-118">A opção `-link` instrui o compilador a inserir as informações de tipo de COM do assembly de interoperabilidade referenciado no código compilado resultante.</span><span class="sxs-lookup"><span data-stu-id="b8750-118">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="b8750-119">O tipo COM é identificado pelo valor CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="b8750-119">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="b8750-120">Como resultado, o aplicativo pode ser executado em um computador de destino que tem os mesmos tipos COM instalados com os mesmos valores CLSID.</span><span class="sxs-lookup"><span data-stu-id="b8750-120">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="b8750-121">Os aplicativos que automatizam o Microsoft Office são um bom exemplo.</span><span class="sxs-lookup"><span data-stu-id="b8750-121">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="b8750-122">Como aplicativos como o Office normalmente mantêm o mesmo valor CLSID entre diferentes versões, seu aplicativo pode usar os tipos COM referenciados contanto que o .NET Framework 4 ou posterior esteja instalado no computador de destino e seu aplicativo use métodos, propriedades ou eventos que estão incluídos nos tipos COM referenciados.</span><span class="sxs-lookup"><span data-stu-id="b8750-122">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="b8750-123">A opção `-link` incorpora apenas interfaces, estruturas e delegados.</span><span class="sxs-lookup"><span data-stu-id="b8750-123">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="b8750-124">Não há suporte para a inserção de classes COM.</span><span class="sxs-lookup"><span data-stu-id="b8750-124">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8750-125">Quando você cria uma instância de um tipo COM inserido no seu código, você deve criar a instância usando a interface apropriada.</span><span class="sxs-lookup"><span data-stu-id="b8750-125">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="b8750-126">Tentar criar uma instância de um tipo COM inserido usando o CoClass causa um erro.</span><span class="sxs-lookup"><span data-stu-id="b8750-126">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="b8750-127">Para definir a opção `-link` em Visual Studio, adicione uma referência de assembly e defina a propriedade `Embed Interop Types` como **true**.</span><span class="sxs-lookup"><span data-stu-id="b8750-127">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="b8750-128">O valor padrão da propriedade `Embed Interop Types` é **false**.</span><span class="sxs-lookup"><span data-stu-id="b8750-128">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="b8750-129">Se você vincular a um assembly COM (Assembly A) que em si faz referência a outro assembly COM (Assembly B), também precisará vincular ao Assembly B se uma das seguintes opções for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="b8750-129">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="b8750-130">Um tipo do Assembly A herda de um tipo ou implementa uma interface do Assembly B.</span><span class="sxs-lookup"><span data-stu-id="b8750-130">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="b8750-131">Um campo, propriedade, evento ou método que tem um tipo de retorno ou de parâmetro do Assembly B é invocado.</span><span class="sxs-lookup"><span data-stu-id="b8750-131">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="b8750-132">Use [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) para especificar o diretório em que uma ou mais das suas referências do assembly estão localizado.</span><span class="sxs-lookup"><span data-stu-id="b8750-132">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="b8750-133">Como o [/Reference](../../../visual-basic/reference/command-line-compiler/reference.md) opção de compilador, o `-link` opção de compilador usa o arquivo de resposta Vbc, que as referências usadas com frequência [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span><span class="sxs-lookup"><span data-stu-id="b8750-133">Like the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span> <span data-ttu-id="b8750-134">Use o [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) opção de compilador se você não quiser que o compilador a usar o arquivo Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="b8750-134">Use the [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="b8750-135">A forma abreviada de `-link` é `-l`.</span><span class="sxs-lookup"><span data-stu-id="b8750-135">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="b8750-136">Tipos genéricos e inseridos</span><span class="sxs-lookup"><span data-stu-id="b8750-136">Generics and Embedded Types</span></span>  
 <span data-ttu-id="b8750-137">As seções a seguir descrevem as limitações no uso de tipos genéricos em aplicativos que inserem tipos de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="b8750-137">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="b8750-138">Interfaces genéricas</span><span class="sxs-lookup"><span data-stu-id="b8750-138">Generic Interfaces</span></span>  
 <span data-ttu-id="b8750-139">As interfaces genéricas que são inseridas de um assembly de interoperabilidade não podem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="b8750-139">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="b8750-140">Isso é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b8750-140">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="b8750-141">Tipos que têm parâmetros genéricos</span><span class="sxs-lookup"><span data-stu-id="b8750-141">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="b8750-142">Os tipos que têm um parâmetro genérico cujo tipo é inserido de um assembly de interoperabilidade não poderão ser usados se o tipo for de um assembly externo.</span><span class="sxs-lookup"><span data-stu-id="b8750-142">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="b8750-143">Essa restrição não se aplica a interfaces.</span><span class="sxs-lookup"><span data-stu-id="b8750-143">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="b8750-144">Por exemplo, considere a interface <xref:Microsoft.Office.Interop.Excel.Range> que é definida no assembly <xref:Microsoft.Office.Interop.Excel>.</span><span class="sxs-lookup"><span data-stu-id="b8750-144">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="b8750-145">Se uma biblioteca insere tipos de interoperabilidade do assembly <xref:Microsoft.Office.Interop.Excel> e expõe um método que retorna um tipo genérico que tem um parâmetro cujo tipo é a interface <xref:Microsoft.Office.Interop.Excel.Range>, esse método deve retornar uma interface genérica, como mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b8750-145">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 <span data-ttu-id="b8750-146">No exemplo a seguir, o código do cliente pode chamar o método que retorna a interface genérica <xref:System.Collections.IList> sem erros.</span><span class="sxs-lookup"><span data-stu-id="b8750-146">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="b8750-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8750-147">Example</span></span>  
 <span data-ttu-id="b8750-148">A linha de comando a seguir compila o arquivo de origem `OfficeApp.vb` e fazer referência a assemblies `COMData1.dll` e `COMData2.dll` para produzir `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="b8750-148">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8750-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8750-149">See Also</span></span>  
 [<span data-ttu-id="b8750-150">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b8750-150">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="b8750-151">Instruções passo a passo: inserindo tipos de assemblies gerenciados</span><span class="sxs-lookup"><span data-stu-id="b8750-151">Walkthrough: Embedding Types from Managed Assemblies</span></span>](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="b8750-152">-referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8750-152">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="b8750-153">-noconfig</span><span class="sxs-lookup"><span data-stu-id="b8750-153">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="b8750-154">-libpath</span><span class="sxs-lookup"><span data-stu-id="b8750-154">-libpath</span></span>](../../../visual-basic/reference/command-line-compiler/libpath.md)  
 [<span data-ttu-id="b8750-155">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8750-155">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="b8750-156">Introdução à Interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="b8750-156">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
