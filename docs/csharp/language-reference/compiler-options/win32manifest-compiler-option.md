---
title: "-win32manifest (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 40b1fa1f9aa465a56eccaf5fff5cf7bb59144e85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="win32manifest-c-compiler-options"></a><span data-ttu-id="64b5d-102">/win32manifest (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="64b5d-102">/win32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="64b5d-103">Use a opção **/win32manifest** para especificar um arquivo de manifesto do aplicativo Win32 para ser inserido em um arquivo PE do projeto.</span><span class="sxs-lookup"><span data-stu-id="64b5d-103">Use the **/win32manifest** option to specify a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64b5d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64b5d-104">Syntax</span></span>  
  
```console  
/win32manifest: filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="64b5d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="64b5d-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="64b5d-106">O nome e o local do arquivo de manifesto personalizado.</span><span class="sxs-lookup"><span data-stu-id="64b5d-106">The name and location of the custom manifest file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64b5d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="64b5d-107">Remarks</span></span>  
 <span data-ttu-id="64b5d-108">Por padrão, o compilador [!INCLUDE[csharp_current_short](~/includes/csharp-current-short-md.md)] insere um manifesto de aplicativo que especifica um nível de execução solicitado de "asInvoker".</span><span class="sxs-lookup"><span data-stu-id="64b5d-108">By default, the [!INCLUDE[csharp_current_short](~/includes/csharp-current-short-md.md)] compiler embeds an application manifest that specifies a requested execution level of "asInvoker."</span></span> <span data-ttu-id="64b5d-109">Ele cria o manifesto na mesma pasta em que o executável é compilado, normalmente a pasta bin\Debug ou bin\Release quando você usa o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="64b5d-109">It creates the manifest in the same folder in which the executable is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="64b5d-110">Se você quiser fornecer um manifesto personalizado, por exemplo, para especificar um nível de execução solicitado de "highestAvailable" ou "requireAdministrator", use esta opção para especificar o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="64b5d-110">If you want to supply a custom manifest, for example to specify a requested execution level of "highestAvailable" or "requireAdministrator," use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64b5d-111">Essa opção e a opção [/win32res (opções do compilador C#)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) opção são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="64b5d-111">This option and the [/win32res (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) option are mutually exclusive.</span></span> <span data-ttu-id="64b5d-112">Se você tentar usar ambas as opções na mesma linha de comando, você obterá um erro de build.</span><span class="sxs-lookup"><span data-stu-id="64b5d-112">If you try to use both options in the same command line you will get a build error.</span></span>  
  
 <span data-ttu-id="64b5d-113">Um aplicativo que não tem nenhum aplicativo de manifesto que especifica que um nível de execução solicitado estará sujeito a virtualização de arquivo/registro sob o recurso de controle de conta de usuário do Windows.</span><span class="sxs-lookup"><span data-stu-id="64b5d-113">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows.</span></span> <span data-ttu-id="64b5d-114">Para obter mais informações, consulte [User Account Control](/windows/access-protection/user-account-control/user-account-control-overview).</span><span class="sxs-lookup"><span data-stu-id="64b5d-114">For more information, see [User Account Control](/windows/access-protection/user-account-control/user-account-control-overview).</span></span>  
  
 <span data-ttu-id="64b5d-115">Seu aplicativo estará sujeito à virtualização se alguma dessas condições for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="64b5d-115">Your application will be subject to virtualization if either of these conditions is true:</span></span>  
  
-   <span data-ttu-id="64b5d-116">Você usa a opção **/nowin32manifest** e não fornece um manifesto em uma etapa de build posterior ou como parte de um arquivo do Recurso do Windows (.res) usando a opção **/win32res**.</span><span class="sxs-lookup"><span data-stu-id="64b5d-116">You use the **/nowin32manifest** option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the **/win32res** option.</span></span>  
  
-   <span data-ttu-id="64b5d-117">Você fornece um manifesto personalizado que não especifica um nível de execução solicitado.</span><span class="sxs-lookup"><span data-stu-id="64b5d-117">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="64b5d-118"> cria um arquivo .manifest padrão e o armazena nos diretórios de depuração e liberação juntamente com o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="64b5d-118"> creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="64b5d-119">Você pode adicionar um manifesto personalizado criando um em qualquer editor de texto e, em seguida, adicionando o arquivo ao projeto.</span><span class="sxs-lookup"><span data-stu-id="64b5d-119">You can add a custom manifest by creating one in any text editor and then adding the file to the project.</span></span> <span data-ttu-id="64b5d-120">Como alternativa, você pode clicar com o botão direito do mouse no ícone **Projeto** no **Gerenciador de Soluções**, clicar em **Adicionar Novo Item** e clicar em **Arquivo de Manifesto do Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="64b5d-120">Alternatively, you can right-click the **Project** icon in **Solution Explorer**, click **Add New Item**, and then click **Application Manifest File**.</span></span> <span data-ttu-id="64b5d-121">Depois de adicionar o arquivo de manifesto novo ou existente, ele aparecerá na lista suspensa **Manifesto**.</span><span class="sxs-lookup"><span data-stu-id="64b5d-121">After you have added your new or existing manifest file, it will appear in the **Manifest** drop down list.</span></span> <span data-ttu-id="64b5d-122">Para obter mais informações, consulte [Página Aplicativo, Designer de Projeto (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="64b5d-122">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="64b5d-123">Você pode fornecer o manifesto do aplicativo como uma etapa de pós-build personalizada ou como parte de um arquivo de recurso Win32 usando a opção [/nowin32manifest (opções do compilador C#)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="64b5d-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the [/nowin32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) option.</span></span> <span data-ttu-id="64b5d-124">Use essa mesma opção se quiser que o aplicativo seja sujeito à virtualização de arquivo ou Registro no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="64b5d-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="64b5d-125">Isso impedirá que o compilador crie e insira um manifesto padrão no arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="64b5d-125">This will prevent the compiler from creating and embedding a default manifest in the portable executable (PE) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64b5d-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64b5d-126">Example</span></span>  
 <span data-ttu-id="64b5d-127">O exemplo a seguir mostra o manifesto padrão que o Compilador do Visual C# insere em um PE.</span><span class="sxs-lookup"><span data-stu-id="64b5d-127">The following example shows the default manifest that the Visual C# compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64b5d-128">O compilador insere um nome de aplicativo padrão "MyApplication" no xml.</span><span class="sxs-lookup"><span data-stu-id="64b5d-128">The compiler inserts a standard application name " MyApplication.app " into the xml.</span></span> <span data-ttu-id="64b5d-129">Essa é uma solução alternativa para habilitar os aplicativos para serem executados no Windows Server 2003 Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="64b5d-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="64b5d-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64b5d-130">See Also</span></span>  
 [<span data-ttu-id="64b5d-131">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="64b5d-131">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="64b5d-132">/nowin32manifest (opções do compilador c#)</span><span class="sxs-lookup"><span data-stu-id="64b5d-132">/nowin32manifest (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)  
 [<span data-ttu-id="64b5d-133">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="64b5d-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
