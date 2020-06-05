---
title: -reference
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 633b457106203e213f5d30003e576b7e8132f4d2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400481"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="0886e-102">-referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0886e-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="0886e-103">Faz com que o compilador transforme informações de tipo nos assemblies especificados disponíveis para o projeto que você está compilando no momento.</span><span class="sxs-lookup"><span data-stu-id="0886e-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0886e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0886e-104">Syntax</span></span>  
  
```console  
-reference:fileList  
```

<span data-ttu-id="0886e-105">ou</span><span class="sxs-lookup"><span data-stu-id="0886e-105">or</span></span>

```console
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="0886e-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="0886e-106">Arguments</span></span>  
  
|<span data-ttu-id="0886e-107">Termo</span><span class="sxs-lookup"><span data-stu-id="0886e-107">Term</span></span>|<span data-ttu-id="0886e-108">Definição</span><span class="sxs-lookup"><span data-stu-id="0886e-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="0886e-109">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="0886e-109">Required.</span></span> <span data-ttu-id="0886e-110">Lista delimitada por vírgulas de nomes de arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="0886e-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="0886e-111">Se o nome do arquivo contém um espaço, coloque o nome entre aspas.</span><span class="sxs-lookup"><span data-stu-id="0886e-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0886e-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="0886e-112">Remarks</span></span>  
 <span data-ttu-id="0886e-113">Os arquivos que você importar devem conter metadados de assembly.</span><span class="sxs-lookup"><span data-stu-id="0886e-113">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="0886e-114">Somente tipos públicos são visíveis fora do assembly.</span><span class="sxs-lookup"><span data-stu-id="0886e-114">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="0886e-115">A opção [-addmodule](addmodule.md) importa os metadados de um módulo.</span><span class="sxs-lookup"><span data-stu-id="0886e-115">The [-addmodule](addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="0886e-116">Se você referenciar um assembly (assembly A) que, por sua vez, faz referência a outro assembly (assembly B), você precisará referenciar o assembly B se:</span><span class="sxs-lookup"><span data-stu-id="0886e-116">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="0886e-117">Um tipo do Assembly A herda de um tipo ou implementa uma interface do Assembly B.</span><span class="sxs-lookup"><span data-stu-id="0886e-117">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="0886e-118">Um campo, propriedade, evento ou método que tem um tipo de retorno ou de parâmetro do Assembly B é invocado.</span><span class="sxs-lookup"><span data-stu-id="0886e-118">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="0886e-119">Use [-LIBPATH](libpath.md) para especificar o diretório no qual uma ou mais das suas referências de assembly estão localizadas.</span><span class="sxs-lookup"><span data-stu-id="0886e-119">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="0886e-120">Para que o compilador reconheça um tipo em um assembly (não um módulo), ele deve ser forçado a resolver o tipo.</span><span class="sxs-lookup"><span data-stu-id="0886e-120">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="0886e-121">Um exemplo de como você pode fazer isso é definir uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="0886e-121">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="0886e-122">Outras maneiras estão disponíveis para resolver nomes de tipo em um assembly para o compilador.</span><span class="sxs-lookup"><span data-stu-id="0886e-122">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="0886e-123">Por exemplo, se você herdar de um tipo em um assembly, o nome do tipo será conhecido pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="0886e-123">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="0886e-124">O arquivo de resposta Vbc. rsp, que faz referência a assemblies de .NET Framework comumente usados, é usado por padrão.</span><span class="sxs-lookup"><span data-stu-id="0886e-124">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="0886e-125">Use `-noconfig` se você não quiser que o compilador use Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="0886e-125">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="0886e-126">A forma abreviada de `-reference` é `-r`.</span><span class="sxs-lookup"><span data-stu-id="0886e-126">The short form of `-reference` is `-r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0886e-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0886e-127">Example</span></span>  
 <span data-ttu-id="0886e-128">O comando a seguir compila o arquivo `Input.vb` de origem e os assemblies de referência de `Metad1.dll` e `Metad2.dll` para produzir `Out.exe` .</span><span class="sxs-lookup"><span data-stu-id="0886e-128">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0886e-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="0886e-129">See also</span></span>

- [<span data-ttu-id="0886e-130">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0886e-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="0886e-131">-noconfig</span><span class="sxs-lookup"><span data-stu-id="0886e-131">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="0886e-132">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0886e-132">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="0886e-133">Pública</span><span class="sxs-lookup"><span data-stu-id="0886e-133">Public</span></span>](../../language-reference/modifiers/public.md)
- [<span data-ttu-id="0886e-134">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="0886e-134">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
