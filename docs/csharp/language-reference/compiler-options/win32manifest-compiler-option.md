---
title: -win32manifest (opções do compilador C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8631477f7067870ca1d8a62513489cdbbbe43f33
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="-win32manifest-c-compiler-options"></a><span data-ttu-id="d1f2a-102">-win32manifest (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="d1f2a-102">-win32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="d1f2a-103">Use a opção **-win32manifest** para especificar um arquivo de manifesto do aplicativo Win32 definido pelo usuário para ser inserido em um arquivo PE do projeto.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-103">Use the **-win32manifest** option to specify a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1f2a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1f2a-104">Syntax</span></span>  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="d1f2a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d1f2a-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="d1f2a-106">O nome e o local do arquivo de manifesto personalizado.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-106">The name and location of the custom manifest file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1f2a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d1f2a-107">Remarks</span></span>  
 <span data-ttu-id="d1f2a-108">Por padrão, o compilador do Visual C# insere um manifesto do aplicativo que especifica o nível de execução solicitado "asInvoker".</span><span class="sxs-lookup"><span data-stu-id="d1f2a-108">By default, the Visual C# compiler embeds an application manifest that specifies a requested execution level of "asInvoker."</span></span> <span data-ttu-id="d1f2a-109">Ele cria o manifesto na mesma pasta em que o executável é compilado, normalmente a pasta bin\Debug ou bin\Release quando você usa o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-109">It creates the manifest in the same folder in which the executable is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="d1f2a-110">Se você quiser fornecer um manifesto personalizado, por exemplo, para especificar um nível de execução solicitado de "highestAvailable" ou "requireAdministrator", use esta opção para especificar o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-110">If you want to supply a custom manifest, for example to specify a requested execution level of "highestAvailable" or "requireAdministrator," use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1f2a-111">Essa opção e a opção [-win32res (opções do compilador do C#)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-111">This option and the [-win32res (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) option are mutually exclusive.</span></span> <span data-ttu-id="d1f2a-112">Se você tentar usar ambas as opções na mesma linha de comando, você obterá um erro de build.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-112">If you try to use both options in the same command line you will get a build error.</span></span>  
  
 <span data-ttu-id="d1f2a-113">Um aplicativo que não tem nenhum manifesto do aplicativo que especifica um nível de execução solicitado estará sujeito à virtualização de arquivos/Registro sob o recurso Controle de Conta de Usuário no Windows.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-113">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows.</span></span> <span data-ttu-id="d1f2a-114">Para obter mais informações, consulte [Controle de Conta de Usuário](/windows/access-protection/user-account-control/user-account-control-overview).</span><span class="sxs-lookup"><span data-stu-id="d1f2a-114">For more information, see [User Account Control](/windows/access-protection/user-account-control/user-account-control-overview).</span></span>  
  
 <span data-ttu-id="d1f2a-115">Seu aplicativo estará sujeito à virtualização se alguma dessas condições for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="d1f2a-115">Your application will be subject to virtualization if either of these conditions is true:</span></span>  
  
-   <span data-ttu-id="d1f2a-116">Você usa a opção **-nowin32manifest** e não fornece um manifesto em uma etapa de build posterior ou como parte de um arquivo de Recurso (.res) do Windows usando a opção **-win32res**.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-116">You use the **-nowin32manifest** option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the **-win32res** option.</span></span>  
  
-   <span data-ttu-id="d1f2a-117">Você fornece um manifesto personalizado que não especifica um nível de execução solicitado.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-117">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="d1f2a-118">O Visual Studio cria um arquivo .manifest padrão e o armazena nos diretórios de depuração e liberação juntamente com o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-118">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="d1f2a-119">Você pode adicionar um manifesto personalizado criando um em qualquer editor de texto e, em seguida, adicionando o arquivo ao projeto.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-119">You can add a custom manifest by creating one in any text editor and then adding the file to the project.</span></span> <span data-ttu-id="d1f2a-120">Como alternativa, você pode clicar com o botão direito do mouse no ícone **Projeto** no **Gerenciador de Soluções**, clicar em **Adicionar Novo Item** e clicar em **Arquivo de Manifesto do Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-120">Alternatively, you can right-click the **Project** icon in **Solution Explorer**, click **Add New Item**, and then click **Application Manifest File**.</span></span> <span data-ttu-id="d1f2a-121">Depois de adicionar o arquivo de manifesto novo ou existente, ele aparecerá na lista suspensa **Manifesto**.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-121">After you have added your new or existing manifest file, it will appear in the **Manifest** drop down list.</span></span> <span data-ttu-id="d1f2a-122">Para obter mais informações, consulte [Página Aplicativo, Designer de Projeto (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="d1f2a-122">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="d1f2a-123">Você pode fornecer o manifesto do aplicativo como uma etapa de pós-build personalizada ou como parte de um arquivo de recurso Win32 usando a opção [-nowin32manifest (opções do compilador do C#)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d1f2a-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the [-nowin32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) option.</span></span> <span data-ttu-id="d1f2a-124">Use essa mesma opção se quiser que o aplicativo seja sujeito à virtualização de arquivo ou Registro no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="d1f2a-125">Isso impedirá que o compilador crie e insira um manifesto padrão no arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-125">This will prevent the compiler from creating and embedding a default manifest in the portable executable (PE) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1f2a-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d1f2a-126">Example</span></span>  
 <span data-ttu-id="d1f2a-127">O exemplo a seguir mostra o manifesto padrão que o Compilador do Visual C# insere em um PE.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-127">The following example shows the default manifest that the Visual C# compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1f2a-128">O compilador insere um nome de aplicativo padrão "MyApplication" no xml.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-128">The compiler inserts a standard application name " MyApplication.app " into the xml.</span></span> <span data-ttu-id="d1f2a-129">Essa é uma solução alternativa para habilitar os aplicativos para serem executados no Windows Server 2003 Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="d1f2a-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d1f2a-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1f2a-130">See Also</span></span>  
 [<span data-ttu-id="d1f2a-131">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="d1f2a-131">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="d1f2a-132">-nowin32manifest (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="d1f2a-132">-nowin32manifest (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)  
 [<span data-ttu-id="d1f2a-133">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="d1f2a-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
