---
title: Compilador de XSLT (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 729e6caa36ed8c2f6e77153f8d8ae356513b0603
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956987"
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="0efe2-102">Compilador de XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="0efe2-102">XSLT Compiler (xsltc.exe)</span></span>
<span data-ttu-id="0efe2-103">O compilador XSLT (xsltc.exe) compila folhas de estilos XSLT e gera um assembly.</span><span class="sxs-lookup"><span data-stu-id="0efe2-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="0efe2-104">A folha de estilos compilada pode ser passada diretamente para o método <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0efe2-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0efe2-105">Você não pode gerar assemblies assinados com xsltc.exe.</span><span class="sxs-lookup"><span data-stu-id="0efe2-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="0efe2-106">A ferramenta xsltc.exe está incluída no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0efe2-106">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="0efe2-107">para obter mais informações, consulte os [Downloads do Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span><span class="sxs-lookup"><span data-stu-id="0efe2-107">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0efe2-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0efe2-108">Syntax</span></span>  
  
```console  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="0efe2-109">Argumento</span><span class="sxs-lookup"><span data-stu-id="0efe2-109">Argument</span></span>  
  
|<span data-ttu-id="0efe2-110">Argumento</span><span class="sxs-lookup"><span data-stu-id="0efe2-110">Argument</span></span>|<span data-ttu-id="0efe2-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="0efe2-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="0efe2-112">Especifica o nome da folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="0efe2-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="0efe2-113">A folha de estilos deve ser um arquivo local ou estar localizada na intranet.</span><span class="sxs-lookup"><span data-stu-id="0efe2-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="0efe2-114">Opções</span><span class="sxs-lookup"><span data-stu-id="0efe2-114">Options</span></span>  
  
|<span data-ttu-id="0efe2-115">Opção</span><span class="sxs-lookup"><span data-stu-id="0efe2-115">Option</span></span>|<span data-ttu-id="0efe2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="0efe2-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0efe2-117">`/c[lass]:` `name`</span><span class="sxs-lookup"><span data-stu-id="0efe2-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="0efe2-118">Especifica o nome da classe para a folha de estilos a seguir.</span><span class="sxs-lookup"><span data-stu-id="0efe2-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="0efe2-119">O nome da classe pode ser totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="0efe2-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="0efe2-120">O nome da classe utiliza como padrão o nome da folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="0efe2-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="0efe2-121">Por exemplo, se a folha de estilos customers.xsl for compilada, o nome da classe padrão será customers.</span><span class="sxs-lookup"><span data-stu-id="0efe2-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="0efe2-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="0efe2-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="0efe2-123">Especifica se informações de depuração devem ser geradas.</span><span class="sxs-lookup"><span data-stu-id="0efe2-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="0efe2-124">Especificar `+` ou `/debug` faz o compilador gerar informações de depuração e colocá-lo em um arquivo de banco de dados do programa (PDB).</span><span class="sxs-lookup"><span data-stu-id="0efe2-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="0efe2-125">O nome do arquivo PDB gerado é `assemblyName`.pdb.</span><span class="sxs-lookup"><span data-stu-id="0efe2-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="0efe2-126">Especificar `-`, que é aplicado se você não especificar `/debug`, não cria nenhuma informação de depuração.</span><span class="sxs-lookup"><span data-stu-id="0efe2-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="0efe2-127">Um assembly comercial é gerado.</span><span class="sxs-lookup"><span data-stu-id="0efe2-127">A retail assembly is generated.</span></span> <span data-ttu-id="0efe2-128">**Observação:**  A compilação no modo de depuração pode afetar o desempenho do XSLT significativamente.</span><span class="sxs-lookup"><span data-stu-id="0efe2-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="0efe2-129">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="0efe2-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="0efe2-130">Suprime a notificação de direitos autorais do compilador da exibição.</span><span class="sxs-lookup"><span data-stu-id="0efe2-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="0efe2-131">`/platform:` `string`</span><span class="sxs-lookup"><span data-stu-id="0efe2-131">`/platform:` `string`</span></span>|<span data-ttu-id="0efe2-132">Especifica as plataformas nas quais o assembly pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="0efe2-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="0efe2-133">O exemplo a seguir descreve os valores válidos da plataforma:</span><span class="sxs-lookup"><span data-stu-id="0efe2-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="0efe2-134">O `x86` compila o assembly para ser executado pelo Common Language Runtime compatível com x86, de 32 bits</span><span class="sxs-lookup"><span data-stu-id="0efe2-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="0efe2-135">O `x64` compila o assembly para ser executado pelo Common Language Runtime de 64 bits em um computador que oferece suporte ao conjunto de instruções de AMD64 ou EM64T.</span><span class="sxs-lookup"><span data-stu-id="0efe2-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> <span data-ttu-id="0efe2-136">O Itanium compila seu assembly para que ele seja executado pelo Common Language Runtime de 64 bits em um computador que tem um processador Itanium.</span><span class="sxs-lookup"><span data-stu-id="0efe2-136">Itanium compiles your assembly to be run by the 64-bit common language runtime on a computer that has an Itanium processor.</span></span><br /><br /> <span data-ttu-id="0efe2-137">O `anycpu` compila o assembly para ser executado em qualquer plataforma.</span><span class="sxs-lookup"><span data-stu-id="0efe2-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="0efe2-138">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="0efe2-138">This is the default.</span></span>|  
|<span data-ttu-id="0efe2-139">`/out:` `assemblyName`</span><span class="sxs-lookup"><span data-stu-id="0efe2-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="0efe2-140">Especifica o nome do assembly que é a saída.</span><span class="sxs-lookup"><span data-stu-id="0efe2-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="0efe2-141">O nome do assembly tem como padrão o nome da folha de estilos principal ou a primeira folha de estilos se várias folhas de estilos estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="0efe2-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="0efe2-142">Se a folha de estilos contiver scripts, os scripts serão salvos em um assembly separado.</span><span class="sxs-lookup"><span data-stu-id="0efe2-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="0efe2-143">Nomes assembly de script são gerados do nome do assembly principal.</span><span class="sxs-lookup"><span data-stu-id="0efe2-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="0efe2-144">Por exemplo, se você especificou CustOrders.dll para o nome do assembly, o primeiro assembly de script será chamado CustOrders_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="0efe2-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="0efe2-145">`/settings:` `document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="0efe2-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="0efe2-146">Especifica se deve permitir funções `document()`, script XSLT ou definição de tipo de documento (DTD) na folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="0efe2-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="0efe2-147">O comportamento padrão desabilita o suporte para DTD, a função `document()` e script.</span><span class="sxs-lookup"><span data-stu-id="0efe2-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="0efe2-148">`@` `file`</span><span class="sxs-lookup"><span data-stu-id="0efe2-148">`@` `file`</span></span>|<span data-ttu-id="0efe2-149">Permite que você especifique um arquivo que contém as opções do compilador.</span><span class="sxs-lookup"><span data-stu-id="0efe2-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="0efe2-150">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="0efe2-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0efe2-151">Comentários</span><span class="sxs-lookup"><span data-stu-id="0efe2-151">Remarks</span></span>  
 <span data-ttu-id="0efe2-152">As soluções XSLT podem consistir em vários módulos de folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="0efe2-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="0efe2-153">A ferramenta xsltc.exe gera assemblies de folhas de estilos.</span><span class="sxs-lookup"><span data-stu-id="0efe2-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="0efe2-154">Os assemblies podem então ser passados no método <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0efe2-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0efe2-155">Isso pode ajudar a reduzir os custos de desempenho em alguns cenários de implantação de XSLT.</span><span class="sxs-lookup"><span data-stu-id="0efe2-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0efe2-156">Você também deve incluir o assembly compilado como uma referência em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0efe2-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="0efe2-157">A ferramenta xsltc.exe não valida os nomes de classe (`/class:`*name*) nem de assembly (`/out:`*assemblyName*).</span><span class="sxs-lookup"><span data-stu-id="0efe2-157">The xsltc.exe tool does not validate the class (`/class:`*name*) or assembly (`/out:`*assemblyName*) names.</span></span> <span data-ttu-id="0efe2-158">Erros serão lançados pelo Common Language Runtime se os nomes forem inválidos.</span><span class="sxs-lookup"><span data-stu-id="0efe2-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0efe2-159">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0efe2-159">Examples</span></span>  
 <span data-ttu-id="0efe2-160">O comando a seguir compila a folha de estilos e cria um assembly chamado booksort.dll.</span><span class="sxs-lookup"><span data-stu-id="0efe2-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="0efe2-161">O comando a seguir compila a folha de estilos e cria um assembly e o arquivo de PDB que são chamados booksort.dll e booksort.pdb respectivamente.</span><span class="sxs-lookup"><span data-stu-id="0efe2-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```console  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="0efe2-162">O comando a seguir cria uma folha de estilos que contém um elemento msxsl:script e cria dois assemblies chamados calc.dll e calc_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="0efe2-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```console  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="0efe2-163">O comando a seguir permite o processamento de DTD e suporte de script e cria dois assemblies chamados myTest.dll e myTest_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="0efe2-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```console  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="0efe2-164">O comando a seguir compila dois módulos de folha de estilos e cria um único assembly chamado booksort.dll.</span><span class="sxs-lookup"><span data-stu-id="0efe2-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="0efe2-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0efe2-165">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="0efe2-166">Como: Executar uma transformação XSLT usando um assembly</span><span class="sxs-lookup"><span data-stu-id="0efe2-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)
- [<span data-ttu-id="0efe2-167">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="0efe2-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
