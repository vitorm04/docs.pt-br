---
title: "Como configurar componentes do COM baseados no .NET Framework para ativação sem registro"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cb323bfdff40aafa65c050d4d42f66047d63f650
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="31ad8-102">Como configurar componentes do COM baseados no .NET Framework para ativação sem registro</span><span class="sxs-lookup"><span data-stu-id="31ad8-102">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="31ad8-103">A ativação sem registro de componentes baseados no .NET Framework é apenas um pouco mais complicada do que para componentes COM.</span><span class="sxs-lookup"><span data-stu-id="31ad8-103">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="31ad8-104">A instalação exige dois manifestos:</span><span class="sxs-lookup"><span data-stu-id="31ad8-104">The setup requires two manifests:</span></span>  
  
-   <span data-ttu-id="31ad8-105">Os aplicativos COM devem ter um manifesto do aplicativo no estilo Win32 para identificar o componente gerenciado.</span><span class="sxs-lookup"><span data-stu-id="31ad8-105">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
-   <span data-ttu-id="31ad8-106">Os componentes baseados no .NET Framework devem ter um manifesto do componente para obter as informações de ativação necessárias em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="31ad8-106">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="31ad8-107">Este tópico descreve como associar um manifesto do aplicativo a um aplicativo, associar um manifesto do componente a um componente e inserir um manifesto do componente em um assembly.</span><span class="sxs-lookup"><span data-stu-id="31ad8-107">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
### <a name="to-create-an-application-manifest"></a><span data-ttu-id="31ad8-108">Para criar um manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="31ad8-108">To create an application manifest</span></span>  
  
1.  <span data-ttu-id="31ad8-109">Usando um editor de XML, crie (ou modifique) o manifesto do aplicativo pertencente ao aplicativo COM que interopera com um ou mais componentes gerenciados.</span><span class="sxs-lookup"><span data-stu-id="31ad8-109">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2.  <span data-ttu-id="31ad8-110">Insira o seguinte cabeçalho padrão no início do arquivo:</span><span class="sxs-lookup"><span data-stu-id="31ad8-110">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     <span data-ttu-id="31ad8-111">Para obter informações sobre os elementos do manifesto e seus atributos, pesquise “Referência de manifestos do aplicativo” na Biblioteca MSDN.</span><span class="sxs-lookup"><span data-stu-id="31ad8-111">For information about manifest elements and their attributes, search for "Application Manifests Reference" in the MSDN Library.</span></span>  
  
3.  <span data-ttu-id="31ad8-112">Identifique o proprietário do manifesto.</span><span class="sxs-lookup"><span data-stu-id="31ad8-112">Identify the owner of the manifest.</span></span> <span data-ttu-id="31ad8-113">No exemplo a seguir, `myComApp` versão 1 possui o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="31ad8-113">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4.  <span data-ttu-id="31ad8-114">Identifique os assemblies dependentes.</span><span class="sxs-lookup"><span data-stu-id="31ad8-114">Identify dependent assemblies.</span></span> <span data-ttu-id="31ad8-115">No exemplo a seguir, `myComApp` depende de `myManagedComp`.</span><span class="sxs-lookup"><span data-stu-id="31ad8-115">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="x86"   
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myManagedComp"   
                        version="6.0.0.0"   
                        processorArchitecture="X86"   
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5.  <span data-ttu-id="31ad8-116">Salve e nomeie o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="31ad8-116">Save and name the manifest file.</span></span> <span data-ttu-id="31ad8-117">O nome de um manifesto do aplicativo é o nome do executável do assembly seguido pela extensão .manifest.</span><span class="sxs-lookup"><span data-stu-id="31ad8-117">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="31ad8-118">Por exemplo, o nome do arquivo de manifesto do aplicativo para myComApp.exe é myComApp.exe.manifest.</span><span class="sxs-lookup"><span data-stu-id="31ad8-118">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
 <span data-ttu-id="31ad8-119">Você pode instalar um manifesto do aplicativo no mesmo diretório do aplicativo COM.</span><span class="sxs-lookup"><span data-stu-id="31ad8-119">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="31ad8-120">Como alternativa, adicione-o como um recurso ao arquivo .exe do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="31ad8-120">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="31ad8-121">Para obter mais informações, pesquise “Assemblies lado a lado” na Biblioteca MSDN.</span><span class="sxs-lookup"><span data-stu-id="31ad8-121">For additional information, search for "Side-by-side Assemblies" in the MSDN Library.</span></span>  
  
#### <a name="to-create-a-component-manifest"></a><span data-ttu-id="31ad8-122">Para criar um manifesto do componente</span><span class="sxs-lookup"><span data-stu-id="31ad8-122">To create a component manifest</span></span>  
  
1.  <span data-ttu-id="31ad8-123">Usando um editor de XML, crie um manifesto do componente para descrever o assembly gerenciado.</span><span class="sxs-lookup"><span data-stu-id="31ad8-123">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2.  <span data-ttu-id="31ad8-124">Insira o seguinte cabeçalho padrão no início do arquivo:</span><span class="sxs-lookup"><span data-stu-id="31ad8-124">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3.  <span data-ttu-id="31ad8-125">Identifique o proprietário do arquivo.</span><span class="sxs-lookup"><span data-stu-id="31ad8-125">Identify the owner of the file.</span></span> <span data-ttu-id="31ad8-126">O elemento `<assemblyIdentity>` do elemento `<dependentAssembly>` no arquivo de manifesto do aplicativo deve corresponder àquele no manifesto do componente.</span><span class="sxs-lookup"><span data-stu-id="31ad8-126">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="31ad8-127">No exemplo a seguir, `myManagedComp` versão 1.2.3.4 possui o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="31ad8-127">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />  
    ```  
  
4.  <span data-ttu-id="31ad8-128">Identifique cada classe no assembly.</span><span class="sxs-lookup"><span data-stu-id="31ad8-128">Identify each class in the assembly.</span></span> <span data-ttu-id="31ad8-129">Use o elemento `<clrClass>` para identificar cada classe exclusivamente no assembly gerenciado.</span><span class="sxs-lookup"><span data-stu-id="31ad8-129">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="31ad8-130">O elemento, que é um subelemento do elemento `<assembly>`, tem os atributos descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="31ad8-130">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="31ad8-131">Atributo</span><span class="sxs-lookup"><span data-stu-id="31ad8-131">Attribute</span></span>|<span data-ttu-id="31ad8-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="31ad8-132">Description</span></span>|<span data-ttu-id="31ad8-133">Necessária</span><span class="sxs-lookup"><span data-stu-id="31ad8-133">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="31ad8-134">O identificador que especifica a classe a ser ativada.</span><span class="sxs-lookup"><span data-stu-id="31ad8-134">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="31ad8-135">Sim</span><span class="sxs-lookup"><span data-stu-id="31ad8-135">Yes</span></span>|  
    |`description`|<span data-ttu-id="31ad8-136">Uma cadeia de caracteres que informa o usuário sobre o componente.</span><span class="sxs-lookup"><span data-stu-id="31ad8-136">A string that informs the user about the component.</span></span> <span data-ttu-id="31ad8-137">Uma cadeia de caracteres vazia é o padrão.</span><span class="sxs-lookup"><span data-stu-id="31ad8-137">An empty string is the default.</span></span>|<span data-ttu-id="31ad8-138">Não</span><span class="sxs-lookup"><span data-stu-id="31ad8-138">No</span></span>|  
    |`name`|<span data-ttu-id="31ad8-139">Uma cadeia de caracteres que representa a classe gerenciada.</span><span class="sxs-lookup"><span data-stu-id="31ad8-139">A string that represents the managed class.</span></span>|<span data-ttu-id="31ad8-140">Sim</span><span class="sxs-lookup"><span data-stu-id="31ad8-140">Yes</span></span>|  
    |`progid`|<span data-ttu-id="31ad8-141">O identificador a ser usado para a ativação de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="31ad8-141">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="31ad8-142">Não</span><span class="sxs-lookup"><span data-stu-id="31ad8-142">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="31ad8-143">O modelo de threading COM.</span><span class="sxs-lookup"><span data-stu-id="31ad8-143">The COM threading model.</span></span> <span data-ttu-id="31ad8-144">“Ambos” é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="31ad8-144">"Both" is the default value.</span></span>|<span data-ttu-id="31ad8-145">Não</span><span class="sxs-lookup"><span data-stu-id="31ad8-145">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="31ad8-146">Especifica a versão do CLR (Common Language Runtime) a ser usada.</span><span class="sxs-lookup"><span data-stu-id="31ad8-146">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="31ad8-147">Se você não especificar esse atributo e o CLR ainda não estiver carregado, o componente será carregado com o último CLR instalado anterior ao CLR versão 4.</span><span class="sxs-lookup"><span data-stu-id="31ad8-147">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="31ad8-148">Se você especificar v1.0.3705, v1.1.4322 ou v2.0.50727, a versão efetuará roll forward automaticamente até a última versão instalada do CLR anterior ao CLR versão 4 (geralmente, v2.0.50727).</span><span class="sxs-lookup"><span data-stu-id="31ad8-148">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="31ad8-149">Se outra versão do CLR já estiver carregada e a versão especificada puder ser carregada lado a lado no processo, a versão especificada será carregada; caso contrário, o CLR carregado será usado.</span><span class="sxs-lookup"><span data-stu-id="31ad8-149">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="31ad8-150">Isso poderá causar uma falha de carregamento.</span><span class="sxs-lookup"><span data-stu-id="31ad8-150">This might cause a load failure.</span></span>|<span data-ttu-id="31ad8-151">Não</span><span class="sxs-lookup"><span data-stu-id="31ad8-151">No</span></span>|  
    |`tlbid`|<span data-ttu-id="31ad8-152">O identificador da biblioteca de tipos que contém informações sobre a classe.</span><span class="sxs-lookup"><span data-stu-id="31ad8-152">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="31ad8-153">Não</span><span class="sxs-lookup"><span data-stu-id="31ad8-153">No</span></span>|  
  
     <span data-ttu-id="31ad8-154">Todas as marcações de atributo diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="31ad8-154">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="31ad8-155">É possível obter CLSIDs, ProgIDs, modelos de threading e a versão de tempo de execução exibindo a biblioteca de tipos exportada para o assembly com o ObjectViewer OLE/COM (Oleview.exe).</span><span class="sxs-lookup"><span data-stu-id="31ad8-155">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="31ad8-156">O manifesto do componente a seguir identifica duas classes, `testClass1` e `testClass2`.</span><span class="sxs-lookup"><span data-stu-id="31ad8-156">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4" />  
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5.  <span data-ttu-id="31ad8-157">Salve e nomeie o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="31ad8-157">Save and name the manifest file.</span></span> <span data-ttu-id="31ad8-158">O nome de um manifesto do componente é o nome da biblioteca de assemblies seguido pela extensão .manifest.</span><span class="sxs-lookup"><span data-stu-id="31ad8-158">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="31ad8-159">Por exemplo, a myManagedComp.dll é myManagedComp.manifest.</span><span class="sxs-lookup"><span data-stu-id="31ad8-159">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="31ad8-160">É necessário inserir o manifesto do componente como um recurso no assembly.</span><span class="sxs-lookup"><span data-stu-id="31ad8-160">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="31ad8-161">Para inserir um manifesto do componente em um assembly gerenciado</span><span class="sxs-lookup"><span data-stu-id="31ad8-161">To embed a component manifest in a managed assembly</span></span>  
  
1.  <span data-ttu-id="31ad8-162">Crie um script de recurso que contém a seguinte instrução:</span><span class="sxs-lookup"><span data-stu-id="31ad8-162">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="31ad8-163">Nessa instrução, `myManagedComp.manifest` é o nome do manifesto do componente que está sendo inserido.</span><span class="sxs-lookup"><span data-stu-id="31ad8-163">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="31ad8-164">Neste exemplo, o nome do arquivo de script é `myresource.rc`.</span><span class="sxs-lookup"><span data-stu-id="31ad8-164">For this example, the script file name is `myresource.rc`.</span></span>  
  
2.  <span data-ttu-id="31ad8-165">Compile o script usando o Compilador de Recurso do Microsoft Windows (Rc.exe).</span><span class="sxs-lookup"><span data-stu-id="31ad8-165">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="31ad8-166">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="31ad8-166">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="31ad8-167">O Rc.exe gera o arquivo de recurso `myresource.res`.</span><span class="sxs-lookup"><span data-stu-id="31ad8-167">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3.  <span data-ttu-id="31ad8-168">Compile o arquivo de origem do assembly novamente e especifique o arquivo de recurso usando a opção **/win32res**:</span><span class="sxs-lookup"><span data-stu-id="31ad8-168">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     <span data-ttu-id="31ad8-169">Novamente, `myresource.res` é o nome do arquivo de recurso que contém o recurso inserido.</span><span class="sxs-lookup"><span data-stu-id="31ad8-169">Again, `myresource.res` is the name of the resource file containing embedded resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31ad8-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31ad8-170">See Also</span></span>  
 <span data-ttu-id="31ad8-171">[Interoperabilidade COM sem registro](../../../docs/framework/interop/registration-free-com-interop.md) </span><span class="sxs-lookup"><span data-stu-id="31ad8-171">[Registration-Free COM Interop](../../../docs/framework/interop/registration-free-com-interop.md) </span></span>  
 <span data-ttu-id="31ad8-172">[Requisitos da Interoperabilidade COM Sem Registro](http://msdn.microsoft.com/en-us/0c43bc57-eecf-4e6c-8114-490141cce4da) </span><span class="sxs-lookup"><span data-stu-id="31ad8-172">[Requirements for Registration-Free COM Interop](http://msdn.microsoft.com/en-us/0c43bc57-eecf-4e6c-8114-490141cce4da) </span></span>  
 <span data-ttu-id="31ad8-173">[Configurando componentes COM para ativação sem registro](http://msdn.microsoft.com/en-us/bfe9b02f-d964-4784-960e-a1f94692fbfe) </span><span class="sxs-lookup"><span data-stu-id="31ad8-173">[Configuring COM Components for Registration-Free Activation](http://msdn.microsoft.com/en-us/bfe9b02f-d964-4784-960e-a1f94692fbfe) </span></span>  
 [<span data-ttu-id="31ad8-174">Ativação sem registro de componentes baseados no .NET: um passo a passo</span><span class="sxs-lookup"><span data-stu-id="31ad8-174">Registration-Free Activation of .NET-Based Components: A Walkthrough</span></span>](http://go.microsoft.com/fwlink/?LinkId=158812)

