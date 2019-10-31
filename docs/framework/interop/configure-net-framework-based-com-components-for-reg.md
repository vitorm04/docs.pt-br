---
title: Como configurar componentes do COM baseados no .NET Framework para ativação sem registro
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: 61f5f0f3ec9a4386fa12e7511b4a518f2b56a21c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123663"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="22f57-102">Como configurar componentes do COM baseados no .NET Framework para ativação sem registro</span><span class="sxs-lookup"><span data-stu-id="22f57-102">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="22f57-103">A ativação sem registro de componentes baseados no .NET Framework é apenas um pouco mais complicada do que para componentes COM.</span><span class="sxs-lookup"><span data-stu-id="22f57-103">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="22f57-104">A instalação exige dois manifestos:</span><span class="sxs-lookup"><span data-stu-id="22f57-104">The setup requires two manifests:</span></span>  
  
- <span data-ttu-id="22f57-105">Os aplicativos COM devem ter um manifesto do aplicativo no estilo Win32 para identificar o componente gerenciado.</span><span class="sxs-lookup"><span data-stu-id="22f57-105">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
- <span data-ttu-id="22f57-106">Os componentes baseados no .NET Framework devem ter um manifesto do componente para obter as informações de ativação necessárias em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="22f57-106">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="22f57-107">Este tópico descreve como associar um manifesto do aplicativo a um aplicativo, associar um manifesto do componente a um componente e inserir um manifesto do componente em um assembly.</span><span class="sxs-lookup"><span data-stu-id="22f57-107">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
### <a name="to-create-an-application-manifest"></a><span data-ttu-id="22f57-108">Para criar um manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="22f57-108">To create an application manifest</span></span>  
  
1. <span data-ttu-id="22f57-109">Usando um editor de XML, crie (ou modifique) o manifesto do aplicativo pertencente ao aplicativo COM que interopera com um ou mais componentes gerenciados.</span><span class="sxs-lookup"><span data-stu-id="22f57-109">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2. <span data-ttu-id="22f57-110">Insira o seguinte cabeçalho padrão no início do arquivo:</span><span class="sxs-lookup"><span data-stu-id="22f57-110">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     <span data-ttu-id="22f57-111">Para obter informações sobre e elementos de manifesto e seus atributos, confira [Manifestos de aplicativo](/windows/desktop/SbsCs/application-manifests).</span><span class="sxs-lookup"><span data-stu-id="22f57-111">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3. <span data-ttu-id="22f57-112">Identifique o proprietário do manifesto.</span><span class="sxs-lookup"><span data-stu-id="22f57-112">Identify the owner of the manifest.</span></span> <span data-ttu-id="22f57-113">No exemplo a seguir, `myComApp` versão 1 possui o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="22f57-113">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4. <span data-ttu-id="22f57-114">Identifique os assemblies dependentes.</span><span class="sxs-lookup"><span data-stu-id="22f57-114">Identify dependent assemblies.</span></span> <span data-ttu-id="22f57-115">No exemplo a seguir, `myComApp` depende de `myManagedComp`.</span><span class="sxs-lookup"><span data-stu-id="22f57-115">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
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
  
5. <span data-ttu-id="22f57-116">Salve e nomeie o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="22f57-116">Save and name the manifest file.</span></span> <span data-ttu-id="22f57-117">O nome de um manifesto do aplicativo é o nome do executável do assembly seguido pela extensão .manifest.</span><span class="sxs-lookup"><span data-stu-id="22f57-117">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="22f57-118">Por exemplo, o nome do arquivo de manifesto do aplicativo para myComApp.exe é myComApp.exe.manifest.</span><span class="sxs-lookup"><span data-stu-id="22f57-118">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
 <span data-ttu-id="22f57-119">Você pode instalar um manifesto do aplicativo no mesmo diretório do aplicativo COM.</span><span class="sxs-lookup"><span data-stu-id="22f57-119">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="22f57-120">Como alternativa, adicione-o como um recurso ao arquivo .exe do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="22f57-120">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="22f57-121">Para obter informações adicionais, confira [Sobre assemblies lado a lado](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span><span class="sxs-lookup"><span data-stu-id="22f57-121">For additional information, For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
#### <a name="to-create-a-component-manifest"></a><span data-ttu-id="22f57-122">Para criar um manifesto do componente</span><span class="sxs-lookup"><span data-stu-id="22f57-122">To create a component manifest</span></span>  
  
1. <span data-ttu-id="22f57-123">Usando um editor de XML, crie um manifesto do componente para descrever o assembly gerenciado.</span><span class="sxs-lookup"><span data-stu-id="22f57-123">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2. <span data-ttu-id="22f57-124">Insira o seguinte cabeçalho padrão no início do arquivo:</span><span class="sxs-lookup"><span data-stu-id="22f57-124">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3. <span data-ttu-id="22f57-125">Identifique o proprietário do arquivo.</span><span class="sxs-lookup"><span data-stu-id="22f57-125">Identify the owner of the file.</span></span> <span data-ttu-id="22f57-126">O elemento `<assemblyIdentity>` do elemento `<dependentAssembly>` no arquivo de manifesto do aplicativo deve corresponder àquele no manifesto do componente.</span><span class="sxs-lookup"><span data-stu-id="22f57-126">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="22f57-127">No exemplo a seguir, `myManagedComp` versão 1.2.3.4 possui o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="22f57-127">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
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
  
4. <span data-ttu-id="22f57-128">Identifique cada classe no assembly.</span><span class="sxs-lookup"><span data-stu-id="22f57-128">Identify each class in the assembly.</span></span> <span data-ttu-id="22f57-129">Use o elemento `<clrClass>` para identificar cada classe exclusivamente no assembly gerenciado.</span><span class="sxs-lookup"><span data-stu-id="22f57-129">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="22f57-130">O elemento, que é um subelemento do elemento `<assembly>`, tem os atributos descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="22f57-130">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="22f57-131">Atributo</span><span class="sxs-lookup"><span data-stu-id="22f57-131">Attribute</span></span>|<span data-ttu-id="22f57-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="22f57-132">Description</span></span>|<span data-ttu-id="22f57-133">Necessária</span><span class="sxs-lookup"><span data-stu-id="22f57-133">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="22f57-134">O identificador que especifica a classe a ser ativada.</span><span class="sxs-lookup"><span data-stu-id="22f57-134">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="22f57-135">Sim</span><span class="sxs-lookup"><span data-stu-id="22f57-135">Yes</span></span>|  
    |`description`|<span data-ttu-id="22f57-136">Uma cadeia de caracteres que informa o usuário sobre o componente.</span><span class="sxs-lookup"><span data-stu-id="22f57-136">A string that informs the user about the component.</span></span> <span data-ttu-id="22f57-137">Uma cadeia de caracteres vazia é o padrão.</span><span class="sxs-lookup"><span data-stu-id="22f57-137">An empty string is the default.</span></span>|<span data-ttu-id="22f57-138">Não</span><span class="sxs-lookup"><span data-stu-id="22f57-138">No</span></span>|  
    |`name`|<span data-ttu-id="22f57-139">Uma cadeia de caracteres que representa a classe gerenciada.</span><span class="sxs-lookup"><span data-stu-id="22f57-139">A string that represents the managed class.</span></span>|<span data-ttu-id="22f57-140">Sim</span><span class="sxs-lookup"><span data-stu-id="22f57-140">Yes</span></span>|  
    |`progid`|<span data-ttu-id="22f57-141">O identificador a ser usado para a ativação de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="22f57-141">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="22f57-142">Não</span><span class="sxs-lookup"><span data-stu-id="22f57-142">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="22f57-143">O modelo de threading COM.</span><span class="sxs-lookup"><span data-stu-id="22f57-143">The COM threading model.</span></span> <span data-ttu-id="22f57-144">“Ambos” é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="22f57-144">"Both" is the default value.</span></span>|<span data-ttu-id="22f57-145">Não</span><span class="sxs-lookup"><span data-stu-id="22f57-145">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="22f57-146">Especifica a versão do CLR (Common Language Runtime) a ser usada.</span><span class="sxs-lookup"><span data-stu-id="22f57-146">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="22f57-147">Se você não especificar esse atributo e o CLR ainda não estiver carregado, o componente será carregado com o último CLR instalado anterior ao CLR versão 4.</span><span class="sxs-lookup"><span data-stu-id="22f57-147">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="22f57-148">Se você especificar v1.0.3705, v1.1.4322 ou v2.0.50727, a versão efetuará roll forward automaticamente até a última versão instalada do CLR anterior ao CLR versão 4 (geralmente, v2.0.50727).</span><span class="sxs-lookup"><span data-stu-id="22f57-148">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="22f57-149">Se outra versão do CLR já estiver carregada e a versão especificada puder ser carregada lado a lado no processo, a versão especificada será carregada; caso contrário, o CLR carregado será usado.</span><span class="sxs-lookup"><span data-stu-id="22f57-149">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="22f57-150">Isso poderá causar uma falha de carregamento.</span><span class="sxs-lookup"><span data-stu-id="22f57-150">This might cause a load failure.</span></span>|<span data-ttu-id="22f57-151">Não</span><span class="sxs-lookup"><span data-stu-id="22f57-151">No</span></span>|  
    |`tlbid`|<span data-ttu-id="22f57-152">O identificador da biblioteca de tipos que contém informações sobre a classe.</span><span class="sxs-lookup"><span data-stu-id="22f57-152">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="22f57-153">Não</span><span class="sxs-lookup"><span data-stu-id="22f57-153">No</span></span>|  
  
     <span data-ttu-id="22f57-154">Todas as marcações de atributo diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="22f57-154">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="22f57-155">É possível obter CLSIDs, ProgIDs, modelos de threading e a versão de tempo de execução exibindo a biblioteca de tipos exportada para o assembly com o ObjectViewer OLE/COM (Oleview.exe).</span><span class="sxs-lookup"><span data-stu-id="22f57-155">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="22f57-156">O manifesto do componente a seguir identifica duas classes, `testClass1` e `testClass2`.</span><span class="sxs-lookup"><span data-stu-id="22f57-156">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
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
  
5. <span data-ttu-id="22f57-157">Salve e nomeie o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="22f57-157">Save and name the manifest file.</span></span> <span data-ttu-id="22f57-158">O nome de um manifesto do componente é o nome da biblioteca de assemblies seguido pela extensão .manifest.</span><span class="sxs-lookup"><span data-stu-id="22f57-158">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="22f57-159">Por exemplo, a myManagedComp.dll é myManagedComp.manifest.</span><span class="sxs-lookup"><span data-stu-id="22f57-159">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="22f57-160">É necessário inserir o manifesto do componente como um recurso no assembly.</span><span class="sxs-lookup"><span data-stu-id="22f57-160">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="22f57-161">Para inserir um manifesto do componente em um assembly gerenciado</span><span class="sxs-lookup"><span data-stu-id="22f57-161">To embed a component manifest in a managed assembly</span></span>  
  
1. <span data-ttu-id="22f57-162">Crie um script de recurso que contém a seguinte instrução:</span><span class="sxs-lookup"><span data-stu-id="22f57-162">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="22f57-163">Nessa instrução, `myManagedComp.manifest` é o nome do manifesto do componente que está sendo inserido.</span><span class="sxs-lookup"><span data-stu-id="22f57-163">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="22f57-164">Neste exemplo, o nome do arquivo de script é `myresource.rc`.</span><span class="sxs-lookup"><span data-stu-id="22f57-164">For this example, the script file name is `myresource.rc`.</span></span>  
  
2. <span data-ttu-id="22f57-165">Compile o script usando o Compilador de Recurso do Microsoft Windows (Rc.exe).</span><span class="sxs-lookup"><span data-stu-id="22f57-165">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="22f57-166">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="22f57-166">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="22f57-167">O Rc.exe gera o arquivo de recurso `myresource.res`.</span><span class="sxs-lookup"><span data-stu-id="22f57-167">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3. <span data-ttu-id="22f57-168">Compile o arquivo de origem do assembly novamente e especifique o arquivo de recurso usando a opção **/win32res**:</span><span class="sxs-lookup"><span data-stu-id="22f57-168">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    `/win32res:myresource.res`  
  
     <span data-ttu-id="22f57-169">Novamente, `myresource.res` é o nome do arquivo de recurso que contém recursos incorporados.</span><span class="sxs-lookup"><span data-stu-id="22f57-169">Again, `myresource.res` is the name of the resource file containing embedded resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f57-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22f57-170">See also</span></span>

- [<span data-ttu-id="22f57-171">Interoperabilidade COM sem registro</span><span class="sxs-lookup"><span data-stu-id="22f57-171">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)
- <span data-ttu-id="22f57-172">[Requisitos para interoperabilidade COM sem registro](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="22f57-172">[Requirements for Registration-Free COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span></span>
- <span data-ttu-id="22f57-173">[Configurando componentes COM para ativação sem registro](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="22f57-173">[Configuring COM Components for Registration-Free Activation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span></span>
- <span data-ttu-id="22f57-174">[Ativação sem registro de componentes baseados no .NET: um passo a passo](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="22f57-174">[Registration-Free Activation of .NET-Based Components: A Walkthrough](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span></span>
