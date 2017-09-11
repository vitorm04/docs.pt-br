---
title: /win32manifest (Visual Basic) | Documentos do Microsoft
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
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
caps.latest.revision: 9
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
ms.openlocfilehash: 4a9693bd7eb03dee5a2a9f2d43360b963e9fd876
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="win32manifest-visual-basic"></a><span data-ttu-id="87ae5-102">/win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87ae5-102">/win32manifest (Visual Basic)</span></span>
<span data-ttu-id="87ae5-103">Identifica um definido pelo usuário aplicativo arquivo de manifesto Win32 a ser inserido no arquivo PE (portable executable) de um projeto.</span><span class="sxs-lookup"><span data-stu-id="87ae5-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87ae5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87ae5-104">Syntax</span></span>  
  
```  
/win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="87ae5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="87ae5-105">Arguments</span></span>  
  
|<span data-ttu-id="87ae5-106">Termo</span><span class="sxs-lookup"><span data-stu-id="87ae5-106">Term</span></span>|<span data-ttu-id="87ae5-107">Definição</span><span class="sxs-lookup"><span data-stu-id="87ae5-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="87ae5-108">O caminho do arquivo de manifesto personalizado.</span><span class="sxs-lookup"><span data-stu-id="87ae5-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87ae5-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="87ae5-109">Remarks</span></span>  
 <span data-ttu-id="87ae5-110">Por padrão, o compilador Visual Basic insere um manifesto de aplicativo que especifica um nível de execução solicitado de asInvoker.</span><span class="sxs-lookup"><span data-stu-id="87ae5-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="87ae5-111">Cria o manifesto na mesma pasta em que o arquivo executável é criado, normalmente a pasta bin\Debug ou bin\Release quando você usa o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87ae5-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="87ae5-112">Se você quiser fornecer um manifesto personalizado, por exemplo, para especificar um nível de execução solicitado de highestAvailable ou requireAdministrator, use essa opção para especificar o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="87ae5-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87ae5-113">Essa opção e o [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) opção são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="87ae5-113">This option and the [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="87ae5-114">Se você tentar usar ambas as opções na mesma linha de comando, você obterá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="87ae5-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="87ae5-115">Um aplicativo que não tenha nenhum aplicativo de manifesto que especifica que um nível de execução solicitado estará sujeita a virtualização de arquivo/registro sob o recurso de controle de conta de usuário no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="87ae5-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="87ae5-116">Para obter mais informações sobre virtualização, consulte [implantação do ClickOnce no Windows Vista](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="87ae5-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="87ae5-117">Seu aplicativo estará sujeito a virtualização se alguma das seguintes condições for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="87ae5-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1.  <span data-ttu-id="87ae5-118">Você usa o `/nowin32manifest` opção e você não fornecer um manifesto em uma etapa posterior da compilação ou como parte de um arquivo Windows Resource (. res), usando o `/win32resource` opção.</span><span class="sxs-lookup"><span data-stu-id="87ae5-118">You use the `/nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `/win32resource` option.</span></span>  
  
2.  <span data-ttu-id="87ae5-119">Fornecer um manifesto personalizado que não especifica um nível de execução solicitado.</span><span class="sxs-lookup"><span data-stu-id="87ae5-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="87ae5-120">cria um arquivo padrão de manifesto e o armazena nos diretórios de depuração e versão junto do arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="87ae5-120"> creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="87ae5-121">Você pode exibir ou editar o arquivo padrão App clicando **exibir configurações de UAC** sobre o **aplicativo** guia no Designer de projeto.</span><span class="sxs-lookup"><span data-stu-id="87ae5-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="87ae5-122">Para obter mais informações, consulte [página de aplicativo, Designer de projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="87ae5-122">For more information, see [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="87ae5-123">Você pode fornecer o manifesto do aplicativo como uma etapa de pós-compilação personalizada ou como parte de um arquivo de recurso Win32 usando o `/nowin32manifest` opção.</span><span class="sxs-lookup"><span data-stu-id="87ae5-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `/nowin32manifest` option.</span></span> <span data-ttu-id="87ae5-124">Use essa mesma opção se quiser que o aplicativo seja sujeito à virtualização de arquivo ou registro no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="87ae5-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="87ae5-125">Isso impedirá que o compilador crie e incorpore um manifesto padrão no arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="87ae5-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87ae5-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87ae5-126">Example</span></span>  
 <span data-ttu-id="87ae5-127">O exemplo a seguir mostra o manifesto padrão que o compilador Visual Basic insere em um PE.</span><span class="sxs-lookup"><span data-stu-id="87ae5-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87ae5-128">O compilador insere um nome padrão de aplicativo MyApplication no manifesto XML.</span><span class="sxs-lookup"><span data-stu-id="87ae5-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="87ae5-129">Essa é uma solução para habilitar aplicativos executados no Windows Server 2003 Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="87ae5-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="87ae5-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87ae5-130">See Also</span></span>  
 <span data-ttu-id="87ae5-131">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="87ae5-131">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="87ae5-132"> [/nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)</span><span class="sxs-lookup"><span data-stu-id="87ae5-132"> [/nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)</span></span>
