---
title: 'Como: Configurar componentes COM baseados no .NET Framework para ativação sem registro'
description: Configurar. Componentes COM baseados em .net para ativação sem registro. A instalação requer um manifesto de aplicativo em estilo Win32 e um manifesto de componente .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: ad25a79add84e43ba0a8e71a0f48c5ddf65108bd
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554834"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="749a8-104">Como: Configurar componentes COM baseados no .NET Framework para ativação sem registro</span><span class="sxs-lookup"><span data-stu-id="749a8-104">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="749a8-105">A ativação sem registro de componentes baseados no .NET Framework é apenas um pouco mais complicada do que para componentes COM.</span><span class="sxs-lookup"><span data-stu-id="749a8-105">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="749a8-106">A instalação exige dois manifestos:</span><span class="sxs-lookup"><span data-stu-id="749a8-106">The setup requires two manifests:</span></span>  
  
- <span data-ttu-id="749a8-107">Os aplicativos COM devem ter um manifesto do aplicativo no estilo Win32 para identificar o componente gerenciado.</span><span class="sxs-lookup"><span data-stu-id="749a8-107">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
- <span data-ttu-id="749a8-108">Os componentes baseados no .NET Framework devem ter um manifesto do componente para obter as informações de ativação necessárias em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="749a8-108">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="749a8-109">Este tópico descreve como associar um manifesto do aplicativo a um aplicativo, associar um manifesto do componente a um componente e inserir um manifesto do componente em um assembly.</span><span class="sxs-lookup"><span data-stu-id="749a8-109">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
## <a name="create-an-application-manifest"></a><span data-ttu-id="749a8-110">Criar um manifesto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="749a8-110">Create an application manifest</span></span>  
  
1. <span data-ttu-id="749a8-111">Usando um editor de XML, crie (ou modifique) o manifesto do aplicativo pertencente ao aplicativo COM que interopera com um ou mais componentes gerenciados.</span><span class="sxs-lookup"><span data-stu-id="749a8-111">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2. <span data-ttu-id="749a8-112">Insira o seguinte cabeçalho padrão no início do arquivo:</span><span class="sxs-lookup"><span data-stu-id="749a8-112">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
     <span data-ttu-id="749a8-113">Para obter informações sobre e elementos de manifesto e seus atributos, confira [Manifestos de aplicativo](/windows/desktop/SbsCs/application-manifests).</span><span class="sxs-lookup"><span data-stu-id="749a8-113">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3. <span data-ttu-id="749a8-114">Identifique o proprietário do manifesto.</span><span class="sxs-lookup"><span data-stu-id="749a8-114">Identify the owner of the manifest.</span></span> <span data-ttu-id="749a8-115">No exemplo a seguir, `myComApp` versão 1 possui o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="749a8-115">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="msil"
      />
    </assembly>  
    ```  
  
4. <span data-ttu-id="749a8-116">Identifique os assemblies dependentes.</span><span class="sxs-lookup"><span data-stu-id="749a8-116">Identify dependent assemblies.</span></span> <span data-ttu-id="749a8-117">No exemplo a seguir, `myComApp` depende de `myManagedComp`.</span><span class="sxs-lookup"><span data-stu-id="749a8-117">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
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
  
5. <span data-ttu-id="749a8-118">Salve e nomeie o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="749a8-118">Save and name the manifest file.</span></span> <span data-ttu-id="749a8-119">O nome de um manifesto do aplicativo é o nome do executável do assembly seguido pela extensão .manifest.</span><span class="sxs-lookup"><span data-stu-id="749a8-119">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="749a8-120">Por exemplo, o nome do arquivo de manifesto do aplicativo para myComApp.exe é myComApp.exe.manifest.</span><span class="sxs-lookup"><span data-stu-id="749a8-120">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
<span data-ttu-id="749a8-121">Você pode instalar um manifesto do aplicativo no mesmo diretório do aplicativo COM.</span><span class="sxs-lookup"><span data-stu-id="749a8-121">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="749a8-122">Como alternativa, adicione-o como um recurso ao arquivo .exe do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="749a8-122">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="749a8-123">Para obter mais informações, consulte [sobre assemblies lado a lado](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span><span class="sxs-lookup"><span data-stu-id="749a8-123">For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
## <a name="create-a-component-manifest"></a><span data-ttu-id="749a8-124">Criar um manifesto de componente</span><span class="sxs-lookup"><span data-stu-id="749a8-124">Create a component manifest</span></span>  
  
1. <span data-ttu-id="749a8-125">Usando um editor de XML, crie um manifesto do componente para descrever o assembly gerenciado.</span><span class="sxs-lookup"><span data-stu-id="749a8-125">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2. <span data-ttu-id="749a8-126">Insira o seguinte cabeçalho padrão no início do arquivo:</span><span class="sxs-lookup"><span data-stu-id="749a8-126">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
3. <span data-ttu-id="749a8-127">Identifique o proprietário do arquivo.</span><span class="sxs-lookup"><span data-stu-id="749a8-127">Identify the owner of the file.</span></span> <span data-ttu-id="749a8-128">O elemento `<assemblyIdentity>` do elemento `<dependentAssembly>` no arquivo de manifesto do aplicativo deve corresponder àquele no manifesto do componente.</span><span class="sxs-lookup"><span data-stu-id="749a8-128">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="749a8-129">No exemplo a seguir, `myManagedComp` versão 1.2.3.4 possui o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="749a8-129">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />
    </assembly>
    ```  
  
4. <span data-ttu-id="749a8-130">Identifique cada classe no assembly.</span><span class="sxs-lookup"><span data-stu-id="749a8-130">Identify each class in the assembly.</span></span> <span data-ttu-id="749a8-131">Use o elemento `<clrClass>` para identificar cada classe exclusivamente no assembly gerenciado.</span><span class="sxs-lookup"><span data-stu-id="749a8-131">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="749a8-132">O elemento, que é um subelemento do elemento `<assembly>`, tem os atributos descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="749a8-132">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="749a8-133">Atributo</span><span class="sxs-lookup"><span data-stu-id="749a8-133">Attribute</span></span>|<span data-ttu-id="749a8-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="749a8-134">Description</span></span>|<span data-ttu-id="749a8-135">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="749a8-135">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="749a8-136">O identificador que especifica a classe a ser ativada.</span><span class="sxs-lookup"><span data-stu-id="749a8-136">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="749a8-137">Yes</span><span class="sxs-lookup"><span data-stu-id="749a8-137">Yes</span></span>|  
    |`description`|<span data-ttu-id="749a8-138">Uma cadeia de caracteres que informa o usuário sobre o componente.</span><span class="sxs-lookup"><span data-stu-id="749a8-138">A string that informs the user about the component.</span></span> <span data-ttu-id="749a8-139">Uma cadeia de caracteres vazia é o padrão.</span><span class="sxs-lookup"><span data-stu-id="749a8-139">An empty string is the default.</span></span>|<span data-ttu-id="749a8-140">No</span><span class="sxs-lookup"><span data-stu-id="749a8-140">No</span></span>|  
    |`name`|<span data-ttu-id="749a8-141">Uma cadeia de caracteres que representa a classe gerenciada.</span><span class="sxs-lookup"><span data-stu-id="749a8-141">A string that represents the managed class.</span></span>|<span data-ttu-id="749a8-142">Yes</span><span class="sxs-lookup"><span data-stu-id="749a8-142">Yes</span></span>|  
    |`progid`|<span data-ttu-id="749a8-143">O identificador a ser usado para a ativação de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="749a8-143">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="749a8-144">No</span><span class="sxs-lookup"><span data-stu-id="749a8-144">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="749a8-145">O modelo de threading COM.</span><span class="sxs-lookup"><span data-stu-id="749a8-145">The COM threading model.</span></span> <span data-ttu-id="749a8-146">“Ambos” é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="749a8-146">"Both" is the default value.</span></span>|<span data-ttu-id="749a8-147">No</span><span class="sxs-lookup"><span data-stu-id="749a8-147">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="749a8-148">Especifica a versão do CLR (Common Language Runtime) a ser usada.</span><span class="sxs-lookup"><span data-stu-id="749a8-148">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="749a8-149">Se você não especificar esse atributo e o CLR ainda não estiver carregado, o componente será carregado com o último CLR instalado anterior ao CLR versão 4.</span><span class="sxs-lookup"><span data-stu-id="749a8-149">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="749a8-150">Se você especificar v1.0.3705, v1.1.4322 ou v2.0.50727, a versão efetuará roll forward automaticamente até a última versão instalada do CLR anterior ao CLR versão 4 (geralmente, v2.0.50727).</span><span class="sxs-lookup"><span data-stu-id="749a8-150">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="749a8-151">Se outra versão do CLR já estiver carregada e a versão especificada puder ser carregada lado a lado no processo, a versão especificada será carregada; caso contrário, o CLR carregado será usado.</span><span class="sxs-lookup"><span data-stu-id="749a8-151">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="749a8-152">Isso poderá causar uma falha de carregamento.</span><span class="sxs-lookup"><span data-stu-id="749a8-152">This might cause a load failure.</span></span>|<span data-ttu-id="749a8-153">No</span><span class="sxs-lookup"><span data-stu-id="749a8-153">No</span></span>|  
    |`tlbid`|<span data-ttu-id="749a8-154">O identificador da biblioteca de tipos que contém informações sobre a classe.</span><span class="sxs-lookup"><span data-stu-id="749a8-154">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="749a8-155">No</span><span class="sxs-lookup"><span data-stu-id="749a8-155">No</span></span>|  
  
     <span data-ttu-id="749a8-156">Todas as marcações de atributo diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="749a8-156">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="749a8-157">É possível obter CLSIDs, ProgIDs, modelos de threading e a versão de runtime exibindo a biblioteca de tipos exportada para o assembly com o ObjectViewer OLE/COM (Oleview.exe).</span><span class="sxs-lookup"><span data-stu-id="749a8-157">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="749a8-158">O manifesto do componente a seguir identifica duas classes, `testClass1` e `testClass2`.</span><span class="sxs-lookup"><span data-stu-id="749a8-158">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"
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
  
5. <span data-ttu-id="749a8-159">Salve e nomeie o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="749a8-159">Save and name the manifest file.</span></span> <span data-ttu-id="749a8-160">O nome de um manifesto do componente é o nome da biblioteca de assemblies seguido pela extensão .manifest.</span><span class="sxs-lookup"><span data-stu-id="749a8-160">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="749a8-161">Por exemplo, a myManagedComp.dll é myManagedComp.manifest.</span><span class="sxs-lookup"><span data-stu-id="749a8-161">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="749a8-162">É necessário inserir o manifesto do componente como um recurso no assembly.</span><span class="sxs-lookup"><span data-stu-id="749a8-162">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="749a8-163">Para inserir um manifesto do componente em um assembly gerenciado</span><span class="sxs-lookup"><span data-stu-id="749a8-163">To embed a component manifest in a managed assembly</span></span>  
  
1. <span data-ttu-id="749a8-164">Crie um script de recurso que contém a seguinte instrução:</span><span class="sxs-lookup"><span data-stu-id="749a8-164">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="749a8-165">Nessa instrução, `myManagedComp.manifest` é o nome do manifesto do componente que está sendo inserido.</span><span class="sxs-lookup"><span data-stu-id="749a8-165">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="749a8-166">Neste exemplo, o nome do arquivo de script é `myresource.rc`.</span><span class="sxs-lookup"><span data-stu-id="749a8-166">For this example, the script file name is `myresource.rc`.</span></span>  
  
2. <span data-ttu-id="749a8-167">Compile o script usando o Compilador de Recurso do Microsoft Windows (Rc.exe).</span><span class="sxs-lookup"><span data-stu-id="749a8-167">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="749a8-168">No prompt de comando, digite o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="749a8-168">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="749a8-169">O Rc.exe gera o arquivo de recurso `myresource.res`.</span><span class="sxs-lookup"><span data-stu-id="749a8-169">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3. <span data-ttu-id="749a8-170">Compile o arquivo de origem do assembly novamente e especifique o arquivo de recurso usando a opção **/win32res**:</span><span class="sxs-lookup"><span data-stu-id="749a8-170">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    `/win32res:myresource.res`  
  
     <span data-ttu-id="749a8-171">Novamente, `myresource.res` é o nome do arquivo de recurso que contém recursos incorporados.</span><span class="sxs-lookup"><span data-stu-id="749a8-171">Again, `myresource.res` is the name of the resource file containing embedded resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="749a8-172">Confira também</span><span class="sxs-lookup"><span data-stu-id="749a8-172">See also</span></span>

- [<span data-ttu-id="749a8-173">Interoperabilidade COM sem registro</span><span class="sxs-lookup"><span data-stu-id="749a8-173">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)
- <span data-ttu-id="749a8-174">[Requisitos para interoperabilidade COM sem registro](/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="749a8-174">[Requirements for Registration-Free COM Interop](/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span></span>
- <span data-ttu-id="749a8-175">[Configurando componentes COM para ativação sem registro](/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="749a8-175">[Configuring COM Components for Registration-Free Activation](/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span></span>
- <span data-ttu-id="749a8-176">[Ativação sem registro de componentes baseados no .NET: um passo a passo](/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="749a8-176">[Registration-Free Activation of .NET-Based Components: A Walkthrough](/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span></span>
