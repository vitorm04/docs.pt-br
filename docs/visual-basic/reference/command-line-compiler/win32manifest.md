---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 901ea984a8e8e90329953a8936e68f2fc07f8847
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="-win32manifest-visual-basic"></a><span data-ttu-id="fda99-102">-win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fda99-102">-win32manifest (Visual Basic)</span></span>
<span data-ttu-id="fda99-103">Identifica um definido pelo usuário aplicativo arquivo manifesto Win32 a ser inserido no arquivo de PE (executável portátil) do projeto.</span><span class="sxs-lookup"><span data-stu-id="fda99-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fda99-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fda99-104">Syntax</span></span>  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="fda99-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fda99-105">Arguments</span></span>  
  
|<span data-ttu-id="fda99-106">Termo</span><span class="sxs-lookup"><span data-stu-id="fda99-106">Term</span></span>|<span data-ttu-id="fda99-107">Definição</span><span class="sxs-lookup"><span data-stu-id="fda99-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="fda99-108">O caminho do arquivo de manifesto personalizado.</span><span class="sxs-lookup"><span data-stu-id="fda99-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fda99-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fda99-109">Remarks</span></span>  
 <span data-ttu-id="fda99-110">Por padrão, o compilador do Visual Basic incorpora um manifesto de aplicativo que especifica um nível de execução solicitado de asInvoker.</span><span class="sxs-lookup"><span data-stu-id="fda99-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="fda99-111">Cria o manifesto na mesma pasta em que o arquivo executável é criado, normalmente a pasta bin\Debug ou bin\Release quando você usa o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fda99-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="fda99-112">Se você quiser fornecer um manifesto personalizado, por exemplo, para especificar um nível de execução solicitado de highestAvailable ou requireAdministrator, use essa opção para especificar o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="fda99-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fda99-113">Essa opção e o [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) opção são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="fda99-113">This option and the [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="fda99-114">Se você tentar usar ambas as opções na mesma linha de comando, você obterá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="fda99-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="fda99-115">Um aplicativo que não tem nenhum manifesto do aplicativo que especifica que um nível de execução solicitado estará sujeito à virtualização de arquivos/Registro sob o recurso de Controle de Conta de Usuário no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="fda99-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="fda99-116">Para obter mais informações sobre a virtualização, consulte [a implantação do ClickOnce no Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="fda99-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="fda99-117">Seu aplicativo estará sujeito a virtualização se alguma das seguintes condições for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="fda99-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1.  <span data-ttu-id="fda99-118">Você usa o `-nowin32manifest` opção e você não fornecer um manifesto em uma etapa de compilação posterior ou como parte de um arquivo de recurso do Windows (. res), usando o `-win32resource` opção.</span><span class="sxs-lookup"><span data-stu-id="fda99-118">You use the `-nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `-win32resource` option.</span></span>  
  
2.  <span data-ttu-id="fda99-119">Você fornece um manifesto personalizado que não especifica um nível de execução solicitado.</span><span class="sxs-lookup"><span data-stu-id="fda99-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="fda99-120">Visual Studio cria um arquivo de manifesto padrão e armazena em diretórios de depuração e versão junto do arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="fda99-120">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="fda99-121">Você pode exibir ou editar o arquivo App. manifest padrão clicando **exibir configurações de UAC** no **aplicativo** guia no Designer de projeto.</span><span class="sxs-lookup"><span data-stu-id="fda99-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="fda99-122">Para obter mais informações, consulte [Página de aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fda99-122">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="fda99-123">Você pode fornecer o manifesto do aplicativo como uma etapa de pós-compilação personalizada, ou como parte de um arquivo de recurso Win32 usando o `-nowin32manifest` opção.</span><span class="sxs-lookup"><span data-stu-id="fda99-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `-nowin32manifest` option.</span></span> <span data-ttu-id="fda99-124">Use essa mesma opção se quiser que o aplicativo seja sujeito à virtualização de arquivo ou Registro no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="fda99-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="fda99-125">Isso impedirá que o compilador de criar e inserir um manifesto padrão no arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="fda99-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fda99-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fda99-126">Example</span></span>  
 <span data-ttu-id="fda99-127">O exemplo a seguir mostra o manifesto padrão que o compilador do Visual Basic insere em um PE.</span><span class="sxs-lookup"><span data-stu-id="fda99-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fda99-128">O compilador insere um nome padrão de aplicativo MyApplication no manifesto XML.</span><span class="sxs-lookup"><span data-stu-id="fda99-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="fda99-129">Essa é uma solução alternativa para habilitar os aplicativos para serem executados no Windows Server 2003 Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="fda99-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fda99-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fda99-130">See Also</span></span>  
 [<span data-ttu-id="fda99-131">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fda99-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="fda99-132">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fda99-132">-nowin32manifest (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
