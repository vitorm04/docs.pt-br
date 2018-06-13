---
title: -link (opções do compilador C#)
ms.date: 07/20/2015
helpviewer_keywords:
- /l compiler option [C#]
- /link compiler option [C#]
- -l compiler option [C#]
- EmbedInteropTypes
- l compiler option [C#]
- embed interop types [COM Interop]
- -link compiler option [C#]
- link compiler option [C#]
ms.assetid: 00da70c6-9ea1-43c2-86f2-aa7f26c03475
ms.openlocfilehash: 668476beb2eefa7a818f60606443ae06ae26a17d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217201"
---
# <a name="-link-c-compiler-options"></a><span data-ttu-id="82fda-102">-link (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="82fda-102">-link (C# Compiler Options)</span></span>
<span data-ttu-id="82fda-103">Faz com que o compilador disponibilize as informações de tipo COM nos assemblies especificados para o projeto sendo compilado no momento.</span><span class="sxs-lookup"><span data-stu-id="82fda-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82fda-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82fda-104">Syntax</span></span>  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="82fda-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="82fda-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="82fda-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="82fda-106">Required.</span></span> <span data-ttu-id="82fda-107">Lista delimitada por vírgulas de nomes de arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="82fda-107">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="82fda-108">Se o nome do arquivo contém um espaço, coloque o nome entre aspas.</span><span class="sxs-lookup"><span data-stu-id="82fda-108">If the file name contains a space, enclose the name in quotation marks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82fda-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="82fda-109">Remarks</span></span>  
 <span data-ttu-id="82fda-110">A opção `-link` permite que você implante um aplicativo que inseriu informações de tipo.</span><span class="sxs-lookup"><span data-stu-id="82fda-110">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="82fda-111">O aplicativo pode usar tipos em um assembly de tempo de execução que implementa as informações de tipo inseridas sem a necessidade de uma referência ao assembly de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="82fda-111">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="82fda-112">Se forem publicadas várias versões do assembly de tempo de execução, o aplicativo que contém as informações de tipo inseridas poderá trabalhar com as várias versões sem precisar ser recompilado.</span><span class="sxs-lookup"><span data-stu-id="82fda-112">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="82fda-113">Para obter um exemplo, consulte [Instruções passo a passo: Inserindo tipos de assemblies gerenciado](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="82fda-113">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span></span>  
  
 <span data-ttu-id="82fda-114">Usar a opção `-link` é especialmente útil quando você está trabalhando com a interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="82fda-114">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="82fda-115">Você pode inserir tipos COM para que seu aplicativo não precise mais de um PIA (assembly de interoperabilidade primário) no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="82fda-115">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="82fda-116">A opção `-link` instrui o compilador a inserir as informações de tipo de COM do assembly de interoperabilidade referenciado no código compilado resultante.</span><span class="sxs-lookup"><span data-stu-id="82fda-116">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="82fda-117">O tipo COM é identificado pelo valor CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="82fda-117">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="82fda-118">Como resultado, o aplicativo pode ser executado em um computador de destino que tem os mesmos tipos COM instalados com os mesmos valores CLSID.</span><span class="sxs-lookup"><span data-stu-id="82fda-118">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="82fda-119">Os aplicativos que automatizam o Microsoft Office são um bom exemplo.</span><span class="sxs-lookup"><span data-stu-id="82fda-119">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="82fda-120">Como aplicativos como o Office normalmente mantêm o mesmo valor CLSID entre diferentes versões, seu aplicativo pode usar os tipos COM referenciados contanto que o .NET Framework 4 ou posterior esteja instalado no computador de destino e seu aplicativo use métodos, propriedades ou eventos que estão incluídos nos tipos COM referenciados.</span><span class="sxs-lookup"><span data-stu-id="82fda-120">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="82fda-121">A opção `-link` incorpora apenas interfaces, estruturas e delegados.</span><span class="sxs-lookup"><span data-stu-id="82fda-121">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="82fda-122">Não há suporte para a inserção de classes COM.</span><span class="sxs-lookup"><span data-stu-id="82fda-122">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82fda-123">Quando você cria uma instância de um tipo COM inserido no seu código, você deve criar a instância usando a interface apropriada.</span><span class="sxs-lookup"><span data-stu-id="82fda-123">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="82fda-124">Tentar criar uma instância de um tipo COM inserido usando o CoClass causa um erro.</span><span class="sxs-lookup"><span data-stu-id="82fda-124">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="82fda-125">Para definir a opção `-link` em Visual Studio, adicione uma referência de assembly e defina a propriedade `Embed Interop Types` como **true**.</span><span class="sxs-lookup"><span data-stu-id="82fda-125">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="82fda-126">O valor padrão da propriedade `Embed Interop Types` é **false**.</span><span class="sxs-lookup"><span data-stu-id="82fda-126">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="82fda-127">Se você vincular a um assembly COM (Assembly A) que em si faz referência a outro assembly COM (Assembly B), também precisará vincular ao Assembly B se uma das seguintes opções for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="82fda-127">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="82fda-128">Um tipo do Assembly A herda de um tipo ou implementa uma interface do Assembly B.</span><span class="sxs-lookup"><span data-stu-id="82fda-128">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="82fda-129">Um campo, propriedade, evento ou método que tem um tipo de retorno ou de parâmetro do Assembly B é invocado.</span><span class="sxs-lookup"><span data-stu-id="82fda-129">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="82fda-130">Como a opção do compilador [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md), a opção do compilador `-link` usa o arquivo de resposta Csc.rsp, que faz referência a assemblies [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] usados com frequência.</span><span class="sxs-lookup"><span data-stu-id="82fda-130">Like the [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option, the `-link` compiler option uses the Csc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span> <span data-ttu-id="82fda-131">Use a opção do compilador [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) se não quiser que o compilador use o arquivo Csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="82fda-131">Use the [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) compiler option if you do not want the compiler to use the Csc.rsp file.</span></span>  
  
 <span data-ttu-id="82fda-132">A forma abreviada de `-link` é `-l`.</span><span class="sxs-lookup"><span data-stu-id="82fda-132">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="82fda-133">Tipos genéricos e inseridos</span><span class="sxs-lookup"><span data-stu-id="82fda-133">Generics and Embedded Types</span></span>  
 <span data-ttu-id="82fda-134">As seções a seguir descrevem as limitações no uso de tipos genéricos em aplicativos que inserem tipos de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="82fda-134">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="82fda-135">Interfaces genéricas</span><span class="sxs-lookup"><span data-stu-id="82fda-135">Generic Interfaces</span></span>  
 <span data-ttu-id="82fda-136">As interfaces genéricas que são inseridas de um assembly de interoperabilidade não podem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="82fda-136">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="82fda-137">Isso é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="82fda-137">This is shown in the following example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_1.cs)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="82fda-138">Tipos que têm parâmetros genéricos</span><span class="sxs-lookup"><span data-stu-id="82fda-138">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="82fda-139">Os tipos que têm um parâmetro genérico cujo tipo é inserido de um assembly de interoperabilidade não poderão ser usados se o tipo for de um assembly externo.</span><span class="sxs-lookup"><span data-stu-id="82fda-139">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="82fda-140">Essa restrição não se aplica a interfaces.</span><span class="sxs-lookup"><span data-stu-id="82fda-140">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="82fda-141">Por exemplo, considere a interface <xref:Microsoft.Office.Interop.Excel.Range> que é definida no assembly <xref:Microsoft.Office.Interop.Excel>.</span><span class="sxs-lookup"><span data-stu-id="82fda-141">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="82fda-142">Se uma biblioteca insere tipos de interoperabilidade do assembly <xref:Microsoft.Office.Interop.Excel> e expõe um método que retorna um tipo genérico que tem um parâmetro cujo tipo é a interface <xref:Microsoft.Office.Interop.Excel.Range>, esse método deve retornar uma interface genérica, como mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="82fda-142">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_2.cs)]  
[!code-csharp[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_3.cs)]  
[!code-csharp[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_4.cs)]  
  
 <span data-ttu-id="82fda-143">No exemplo a seguir, o código do cliente pode chamar o método que retorna a interface genérica <xref:System.Collections.IList> sem erros.</span><span class="sxs-lookup"><span data-stu-id="82fda-143">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="82fda-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82fda-144">Example</span></span>  
 <span data-ttu-id="82fda-145">O código a seguir compila o arquivo de origem `OfficeApp.cs` e faz referência aos assemblies de `COMData1.dll` e `COMData2.dll` para produzir `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="82fda-145">The following code compiles source file `OfficeApp.cs` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="82fda-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82fda-146">See Also</span></span>  
 [<span data-ttu-id="82fda-147">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="82fda-147">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="82fda-148">Instruções passo a passo: inserindo tipos de assemblies gerenciados</span><span class="sxs-lookup"><span data-stu-id="82fda-148">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [<span data-ttu-id="82fda-149">-reference (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="82fda-149">-reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)  
 [<span data-ttu-id="82fda-150">-noconfig (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="82fda-150">-noconfig (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)  
 [<span data-ttu-id="82fda-151">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="82fda-151">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="82fda-152">Visão geral sobre interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="82fda-152">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)
