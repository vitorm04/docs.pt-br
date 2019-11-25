---
title: Como melhorar o tempo de inicialização dos aplicativos do cliente WCF usando o XmlSerializer
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: ca15d710a30586135f0d030e155b09b63a22ee45
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976059"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="976a1-102">Como melhorar o tempo de inicialização dos aplicativos do cliente WCF usando o XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="976a1-102">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>
<span data-ttu-id="976a1-103">Os serviços e os aplicativos cliente que usam tipos de dados que são serializados usando <xref:System.Xml.Serialization.XmlSerializer> geram e compilam o código de serialização para esses tipos de dados em runtime, o que pode levar a um desempenho de inicialização lento.</span><span class="sxs-lookup"><span data-stu-id="976a1-103">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="976a1-104">O código de serialização pré-gerado somente pode ser usado em aplicativos cliente e não em serviços.</span><span class="sxs-lookup"><span data-stu-id="976a1-104">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="976a1-105">A [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pode melhorar o desempenho de inicialização para esses aplicativos, gerando o código de serialização necessário dos assemblies compilados para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="976a1-105">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="976a1-106">Svcutil. exe gera código de serialização para todos os tipos de dados usados em contratos de serviço no assembly de aplicativo compilado que pode ser serializado usando o <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="976a1-106">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="976a1-107">Os contratos de serviço e operação que usam os <xref:System.Xml.Serialization.XmlSerializer> são marcados com o <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="976a1-107">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="976a1-108">Para gerar o código de serialização XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="976a1-108">To generate XmlSerializer serialization code</span></span>  
  
1. <span data-ttu-id="976a1-109">Compile o código do cliente ou do serviço em um ou mais assemblies.</span><span class="sxs-lookup"><span data-stu-id="976a1-109">Compile your service or client code into one or more assemblies.</span></span>  
  
2. <span data-ttu-id="976a1-110">Abra um prompt de comando do SDK.</span><span class="sxs-lookup"><span data-stu-id="976a1-110">Open an SDK command prompt.</span></span>  
  
3. <span data-ttu-id="976a1-111">No prompt de comando, inicie a ferramenta svcutil. exe usando o formato a seguir.</span><span class="sxs-lookup"><span data-stu-id="976a1-111">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="976a1-112">O argumento `assemblyPath` especifica o caminho para um assembly que contém tipos de contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="976a1-112">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="976a1-113">Svcutil. exe gera código de serialização para todos os tipos de dados usados em contratos de serviço no assembly de aplicativo compilado que pode ser serializado usando o <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="976a1-113">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="976a1-114">Svcutil. exe só pode gerar C# código de serialização.</span><span class="sxs-lookup"><span data-stu-id="976a1-114">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="976a1-115">Um arquivo de código-fonte é gerado para cada assembly de entrada.</span><span class="sxs-lookup"><span data-stu-id="976a1-115">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="976a1-116">Você não pode usar a opção **/Language** para alterar o idioma do código gerado.</span><span class="sxs-lookup"><span data-stu-id="976a1-116">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="976a1-117">Para especificar o caminho para assemblies dependentes, use a opção **/Reference** .</span><span class="sxs-lookup"><span data-stu-id="976a1-117">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4. <span data-ttu-id="976a1-118">Torne o código de serialização gerado disponível para seu aplicativo usando uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="976a1-118">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1. <span data-ttu-id="976a1-119">Compile o código de serialização gerado em um assembly separado com o nome [*assembly original*]. XmlSerializer. dll (por exemplo, MyApp. XmlSerializer. dll).</span><span class="sxs-lookup"><span data-stu-id="976a1-119">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="976a1-120">Seu aplicativo deve ser capaz de carregar o assembly, que deve ser assinado com a mesma chave que o assembly original.</span><span class="sxs-lookup"><span data-stu-id="976a1-120">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="976a1-121">Se você recompilar o assembly original, deverá regenerar o assembly de serialização.</span><span class="sxs-lookup"><span data-stu-id="976a1-121">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2. <span data-ttu-id="976a1-122">Compile o código de serialização gerado em um assembly separado e use o <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> no contrato de serviço que usa o <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="976a1-122">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="976a1-123">Defina as propriedades <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> para apontar para o assembly de serialização compilado.</span><span class="sxs-lookup"><span data-stu-id="976a1-123">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3. <span data-ttu-id="976a1-124">Compile o código de serialização gerado em seu assembly de aplicativo e adicione o <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> ao contrato de serviço que usa o <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="976a1-124">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="976a1-125">Não defina as propriedades <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="976a1-125">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="976a1-126">Assume-se que o assembly de serialização padrão seja o assembly atual.</span><span class="sxs-lookup"><span data-stu-id="976a1-126">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="976a1-127">Para gerar o código de serialização XmlSerializer no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="976a1-127">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1. <span data-ttu-id="976a1-128">Crie os projetos de cliente e serviço WCF no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="976a1-128">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="976a1-129">Em seguida, adicione uma referência de serviço ao projeto do cliente.</span><span class="sxs-lookup"><span data-stu-id="976a1-129">Then, add a service reference to the client project.</span></span>  
  
2. <span data-ttu-id="976a1-130">Adicione um <xref:System.ServiceModel.XmlSerializerFormatAttribute> ao contrato de serviço no arquivo *Reference.cs* no projeto de aplicativo cliente em servicelist \*\* -> \*\* **Reference. svcmap**.</span><span class="sxs-lookup"><span data-stu-id="976a1-130">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="976a1-131">Observe que você precisa mostrar todos os arquivos em **Gerenciador de soluções** para ver esses arquivos.</span><span class="sxs-lookup"><span data-stu-id="976a1-131">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3. <span data-ttu-id="976a1-132">Crie o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="976a1-132">Build the client app.</span></span>  
  
4. <span data-ttu-id="976a1-133">Use a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para criar um arquivo serializador *. cs* gerado previamente usando o comando:</span><span class="sxs-lookup"><span data-stu-id="976a1-133">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="976a1-134">O argumento assemblyPath especifica o caminho para o assembly do cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="976a1-134">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="976a1-135">Como:</span><span class="sxs-lookup"><span data-stu-id="976a1-135">Such as:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="976a1-136">O arquivo *WCFClient.XmlSerializers.dll.cs* será gerado.</span><span class="sxs-lookup"><span data-stu-id="976a1-136">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5. <span data-ttu-id="976a1-137">Compile o assembly de serialização gerado previamente.</span><span class="sxs-lookup"><span data-stu-id="976a1-137">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="976a1-138">Com base no exemplo na etapa anterior, o comando Compile seria o seguinte:</span><span class="sxs-lookup"><span data-stu-id="976a1-138">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```console  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="976a1-139">Verifique se o *WCFClient. XmlSerializer. dll* gerado está no mesmo diretório que o aplicativo cliente, que é *WCFClient. exe* nesse caso.</span><span class="sxs-lookup"><span data-stu-id="976a1-139">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6. <span data-ttu-id="976a1-140">Execute o aplicativo cliente como de costume.</span><span class="sxs-lookup"><span data-stu-id="976a1-140">Run the client app as usual.</span></span> <span data-ttu-id="976a1-141">O assembly de serialização gerado previamente será usado.</span><span class="sxs-lookup"><span data-stu-id="976a1-141">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="976a1-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="976a1-142">Example</span></span>  
 <span data-ttu-id="976a1-143">O comando a seguir gera tipos de serialização para `XmlSerializer` tipos que quaisquer contratos de serviço no assembly usam.</span><span class="sxs-lookup"><span data-stu-id="976a1-143">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```console  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="976a1-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="976a1-144">See also</span></span>

- [<span data-ttu-id="976a1-145">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="976a1-145">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
