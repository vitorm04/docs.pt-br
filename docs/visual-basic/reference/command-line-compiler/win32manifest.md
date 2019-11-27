---
title: -win32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: cef1e6c19e7fdd6fc9f42c8fc36008314ea80a80
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349139"
---
# <a name="-win32manifest-visual-basic"></a><span data-ttu-id="8e7dc-102">-win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e7dc-102">-win32manifest (Visual Basic)</span></span>
<span data-ttu-id="8e7dc-103">Identifica um arquivo de manifesto do aplicativo Win32 definido pelo usuário para ser inserido no arquivo executável portátil (PE) de um projeto.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e7dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e7dc-104">Syntax</span></span>  
  
```console  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="8e7dc-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="8e7dc-105">Arguments</span></span>  
  
|<span data-ttu-id="8e7dc-106">Termo</span><span class="sxs-lookup"><span data-stu-id="8e7dc-106">Term</span></span>|<span data-ttu-id="8e7dc-107">Definição</span><span class="sxs-lookup"><span data-stu-id="8e7dc-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="8e7dc-108">O caminho do arquivo de manifesto personalizado.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e7dc-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e7dc-109">Remarks</span></span>  
 <span data-ttu-id="8e7dc-110">Por padrão, o compilador Visual Basic insere um manifesto do aplicativo que especifica um nível de execução solicitado de asInvoker.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="8e7dc-111">Ele cria o manifesto na mesma pasta em que o arquivo executável é compilado, normalmente a pasta bin\Debug ou bin\Release quando você usa o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="8e7dc-112">Se você quiser fornecer um manifesto personalizado, por exemplo, para especificar um nível de execução solicitado de highestAvailable ou requireAdministrator, use essa opção para especificar o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e7dc-113">Essa opção e a opção [-Win32Resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-113">This option and the [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="8e7dc-114">Se você tentar usar ambas as opções na mesma linha de comando, receberá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="8e7dc-115">Um aplicativo que não tem nenhum manifesto do aplicativo que especifica que um nível de execução solicitado estará sujeito à virtualização de arquivos/Registro sob o recurso de Controle de Conta de Usuário no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="8e7dc-116">Para saber mais sobre virtualização, confira [Implantação do ClickOnce no Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="8e7dc-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="8e7dc-117">Seu aplicativo estará sujeito à virtualização se qualquer uma das seguintes condições for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="8e7dc-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1. <span data-ttu-id="8e7dc-118">Você usa a opção `-nowin32manifest` e não fornece um manifesto em uma etapa de Build posterior ou como parte de um arquivo de recurso do Windows (. res) usando a opção `-win32resource`.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-118">You use the `-nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `-win32resource` option.</span></span>  
  
2. <span data-ttu-id="8e7dc-119">Você fornece um manifesto personalizado que não especifica um nível de execução solicitado.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="8e7dc-120">O Visual Studio cria um arquivo .manifest padrão e o armazena nos diretórios de depuração e liberação juntamente com o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-120">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="8e7dc-121">Você pode exibir ou editar o arquivo app. manifest padrão clicando em **exibir configurações de UAC** na guia **aplicativo** no designer de projeto.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="8e7dc-122">Para obter mais informações, consulte [Página de aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8e7dc-122">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="8e7dc-123">Você pode fornecer o manifesto do aplicativo como uma etapa de pós-compilação personalizada ou como parte de um arquivo de recurso do Win32 usando a opção `-nowin32manifest`.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `-nowin32manifest` option.</span></span> <span data-ttu-id="8e7dc-124">Use essa mesma opção se quiser que o aplicativo seja sujeito à virtualização de arquivo ou Registro no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="8e7dc-125">Isso impedirá que o compilador crie e incorpore um manifesto padrão no arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e7dc-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8e7dc-126">Example</span></span>  
 <span data-ttu-id="8e7dc-127">O exemplo a seguir mostra o manifesto padrão que o Visual Basic compilador insere em um PE.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e7dc-128">O compilador insere um nome de aplicativo padrão MyApplication. app no XML do manifesto.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="8e7dc-129">Essa é uma solução alternativa para habilitar os aplicativos para serem executados no Windows Server 2003 Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="8e7dc-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e7dc-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e7dc-130">See also</span></span>

- [<span data-ttu-id="8e7dc-131">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e7dc-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="8e7dc-132">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e7dc-132">-nowin32manifest (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
