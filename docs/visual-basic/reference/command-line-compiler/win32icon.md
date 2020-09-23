---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: c6d5e054063592db5777a76fe19da79337ed5034
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084951"
---
# <a name="-win32icon"></a><span data-ttu-id="8b688-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="8b688-102">-win32icon</span></span>

<span data-ttu-id="8b688-103">Insere um arquivo. ico no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="8b688-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="8b688-104">Esse arquivo. ico representa o arquivo de saída no **Explorador de arquivos**.</span><span class="sxs-lookup"><span data-stu-id="8b688-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b688-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b688-105">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="8b688-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="8b688-106">Arguments</span></span>  
  
|<span data-ttu-id="8b688-107">Termo</span><span class="sxs-lookup"><span data-stu-id="8b688-107">Term</span></span>|<span data-ttu-id="8b688-108">Definição</span><span class="sxs-lookup"><span data-stu-id="8b688-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="8b688-109">O arquivo. ico a ser adicionado ao arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="8b688-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="8b688-110">Coloque o nome de arquivo entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="8b688-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b688-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b688-111">Remarks</span></span>  

 <span data-ttu-id="8b688-112">Você pode criar um arquivo. ico com o compilador de recursos do Microsoft Windows (RC).</span><span class="sxs-lookup"><span data-stu-id="8b688-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="8b688-113">O compilador de recursos é invocado quando você compila um programa de Visual C++; um arquivo. ico é criado a partir do arquivo. rc.</span><span class="sxs-lookup"><span data-stu-id="8b688-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="8b688-114">As opções `-win32icon` e `-win32resource` são mutualmente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="8b688-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="8b688-115">Consulte [-linkresource (Visual Basic)](linkresource.md) para fazer referência a um arquivo de recurso .NET Framework ou [-Resource (Visual Basic)](resource.md) para anexar um arquivo de recurso de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8b688-115">See [-linkresource (Visual Basic)](linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](resource.md) to attach a .NET Framework resource file.</span></span> <span data-ttu-id="8b688-116">Consulte [-Win32Resource](win32resource.md) para importar um arquivo. res.</span><span class="sxs-lookup"><span data-stu-id="8b688-116">See [-win32resource](win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="8b688-117">Para definir-win32icon no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8b688-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="8b688-118">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="8b688-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8b688-119">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="8b688-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="8b688-120">2. Clique na guia **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="8b688-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="8b688-121">3. modifique o valor na caixa **ícone** .</span><span class="sxs-lookup"><span data-stu-id="8b688-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8b688-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b688-122">Example</span></span>  

 <span data-ttu-id="8b688-123">O código a seguir compila `In.vb` e anexa um arquivo. ico, `Rf.ico` .</span><span class="sxs-lookup"><span data-stu-id="8b688-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b688-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="8b688-124">See also</span></span>

- [<span data-ttu-id="8b688-125">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8b688-125">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="8b688-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b688-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
