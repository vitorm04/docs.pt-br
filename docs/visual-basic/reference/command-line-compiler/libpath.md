---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: b7bfcb0f2034145822922126fe61efea8d8ef269
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344202"
---
# <a name="-libpath"></a><span data-ttu-id="67ba9-102">-libpath</span><span class="sxs-lookup"><span data-stu-id="67ba9-102">-libpath</span></span>
<span data-ttu-id="67ba9-103">Especifica o local dos assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="67ba9-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67ba9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67ba9-104">Syntax</span></span>  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="67ba9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="67ba9-105">Arguments</span></span>  
  
|<span data-ttu-id="67ba9-106">Termo</span><span class="sxs-lookup"><span data-stu-id="67ba9-106">Term</span></span>|<span data-ttu-id="67ba9-107">Definição</span><span class="sxs-lookup"><span data-stu-id="67ba9-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="67ba9-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="67ba9-108">Required.</span></span> <span data-ttu-id="67ba9-109">Lista delimitada por ponto e vírgula de diretórios para o compilador examinar se um assembly referenciado não for encontrada no diretório de trabalho atual (o diretório do qual você está invocando o compilador) ou o diretório do sistema do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="67ba9-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="67ba9-110">Se o nome do diretório contém um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="67ba9-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67ba9-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="67ba9-111">Remarks</span></span>  
 <span data-ttu-id="67ba9-112">O `-libpath` opção especifica o local dos assemblies referenciados pelo [-referência](../../../visual-basic/reference/command-line-compiler/reference.md) opção.</span><span class="sxs-lookup"><span data-stu-id="67ba9-112">The `-libpath` option specifies the location of assemblies referenced by the [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="67ba9-113">O compilador pesquisa referências de assembly que não são totalmente qualificadas na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="67ba9-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="67ba9-114">Diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="67ba9-114">Current working directory.</span></span> <span data-ttu-id="67ba9-115">Esse é o diretório do qual o compilador é invocado.</span><span class="sxs-lookup"><span data-stu-id="67ba9-115">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="67ba9-116">O diretório de sistema do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="67ba9-116">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="67ba9-117">Diretórios especificados pela `/libpath`.</span><span class="sxs-lookup"><span data-stu-id="67ba9-117">Directories specified by `/libpath`.</span></span>  
  
4. <span data-ttu-id="67ba9-118">Diretórios especificados pela variável de ambiente LIB.</span><span class="sxs-lookup"><span data-stu-id="67ba9-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="67ba9-119">O `-libpath` opção é aditivo; especificá-lo mais de uma vez acrescenta a valores anteriores.</span><span class="sxs-lookup"><span data-stu-id="67ba9-119">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="67ba9-120">Use `-reference` para especificar uma referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="67ba9-120">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="67ba9-121">Configurar /libpath no Visual Studio ambiente de desenvolvimento integrado</span><span class="sxs-lookup"><span data-stu-id="67ba9-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="67ba9-122">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="67ba9-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="67ba9-123">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="67ba9-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="67ba9-124">2.  Clique na guia **Referências**.</span><span class="sxs-lookup"><span data-stu-id="67ba9-124">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="67ba9-125">3.  Clique o **caminhos de referência...**  botão.</span><span class="sxs-lookup"><span data-stu-id="67ba9-125">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="67ba9-126">4.  No **caminhos de referência** caixa de diálogo, digite o nome do diretório na **pasta:** caixa.</span><span class="sxs-lookup"><span data-stu-id="67ba9-126">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="67ba9-127">5.  Clique em **adicionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="67ba9-127">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="67ba9-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="67ba9-128">Example</span></span>  
 <span data-ttu-id="67ba9-129">O seguinte código compila `T2.vb` para criar um arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="67ba9-129">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="67ba9-130">O compilador procura no diretório de trabalho, no diretório raiz da unidade c e no diretório da unidade c: novos Assemblies referências de assembly.</span><span class="sxs-lookup"><span data-stu-id="67ba9-130">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="67ba9-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67ba9-131">See also</span></span>

- [<span data-ttu-id="67ba9-132">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="67ba9-132">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="67ba9-133">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="67ba9-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="67ba9-134">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="67ba9-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
