---
title: 'Como: registrar e configurar um moniker de serviço'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: dfac833cc7517af00d0264fc5d11fc83ae543569
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000799"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="310ec-102">Como: registrar e configurar um moniker de serviço</span><span class="sxs-lookup"><span data-stu-id="310ec-102">How to: Register and Configure a Service Moniker</span></span>
<span data-ttu-id="310ec-103">Antes de usar o moniker de serviço do Windows Communication Foundation (WCF) dentro de um aplicativo COM um contrato com tipo, você deve registrar os tipos de atributo necessários com e configurar o aplicativo COM e o identificador de origem com a ligação exigida configuração.</span><span class="sxs-lookup"><span data-stu-id="310ec-103">Before using the Windows Communication Foundation (WCF) service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
### <a name="to-register-the-required-attributed-types-with-com"></a><span data-ttu-id="310ec-104">Para registrar os tipos de atributo necessários COM</span><span class="sxs-lookup"><span data-stu-id="310ec-104">To register the required attributed types with COM</span></span>  
  
1. <span data-ttu-id="310ec-105">Use o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta para recuperar o contrato de metadados do serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="310ec-105">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the WCF service.</span></span> <span data-ttu-id="310ec-106">Isso gera o código-fonte para um assembly de cliente do WCF e um arquivo de configuração de aplicativo do cliente.</span><span class="sxs-lookup"><span data-stu-id="310ec-106">This generates the source code for a WCF client assembly and a client application configuration file.</span></span>  
  
2. <span data-ttu-id="310ec-107">Certifique-se de que os tipos no assembly são marcados como `ComVisible`.</span><span class="sxs-lookup"><span data-stu-id="310ec-107">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="310ec-108">Para fazer isso, adicione o seguinte atributo ao arquivo AssemblyInfo.cs no projeto do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="310ec-108">To do so, add the following attribute to the AssemblyInfo.cs file in your Visual Studio project.</span></span>  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3. <span data-ttu-id="310ec-109">Compile o cliente WCF gerenciado como um assembly de nome forte.</span><span class="sxs-lookup"><span data-stu-id="310ec-109">Compile the managed WCF client as a strong-named assembly.</span></span> <span data-ttu-id="310ec-110">Isso exige a assinar com um par de chaves criptográficas.</span><span class="sxs-lookup"><span data-stu-id="310ec-110">This requires signing with a cryptographic key pair.</span></span> <span data-ttu-id="310ec-111">Para obter mais informações, consulte [assinar um Assembly com um nome forte](https://go.microsoft.com/fwlink/?LinkId=94874) no guia do desenvolvedor do .NET.</span><span class="sxs-lookup"><span data-stu-id="310ec-111">For more information, see [Signing an Assembly with a Strong Name](https://go.microsoft.com/fwlink/?LinkId=94874) in the .NET Developer's Guide.</span></span>  
  
4. <span data-ttu-id="310ec-112">Use a ferramenta de registro do Assembly (Regasm.exe) com o `/tlb` opção registrar os tipos no assembly com COM.</span><span class="sxs-lookup"><span data-stu-id="310ec-112">Use the Assembly Registration (Regasm.exe) tool with the `/tlb` option to register the types in the assembly with COM.</span></span>  
  
5. <span data-ttu-id="310ec-113">Use a ferramenta de Cache de Assembly Global (Gacutil.exe) para adicionar o assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="310ec-113">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="310ec-114">Assinar o assembly e adicioná-lo ao Cache de Assembly Global são etapas opcionais, mas elas podem simplificar o processo de carregar o assembly do local correto no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="310ec-114">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="310ec-115">Para configurar o aplicativo COM e o moniker com a configuração de associação necessários</span><span class="sxs-lookup"><span data-stu-id="310ec-115">To configure the COM application and the moniker with the required binding configuration</span></span>  
  
- <span data-ttu-id="310ec-116">Coloque as definições de associação (gerado pelo [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) no arquivo de configuração do aplicativo cliente gerado) no arquivo de configuração do aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="310ec-116">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="310ec-117">Por exemplo, para um Visual Basic 6.0 executável denominado CallCenterClient.exe, a configuração deve ser colocada em um arquivo chamado CallCenterConfig.exe.config dentro do mesmo diretório que o executável.</span><span class="sxs-lookup"><span data-stu-id="310ec-117">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="310ec-118">O aplicativo cliente agora pode usar o moniker.</span><span class="sxs-lookup"><span data-stu-id="310ec-118">The client application can now use the moniker.</span></span> <span data-ttu-id="310ec-119">Observe que a configuração de associação não será necessária se usando um dos tipos fornecidos pelo WCF de associação padrão.</span><span class="sxs-lookup"><span data-stu-id="310ec-119">Note that the binding configuration is not required if using one of the standard binding types provided by WCF.</span></span>  
  
     <span data-ttu-id="310ec-120">O tipo a seguir está registrado.</span><span class="sxs-lookup"><span data-stu-id="310ec-120">The following type is registered.</span></span>  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     <span data-ttu-id="310ec-121">O aplicativo ficará exposto usando uma `wsHttpBinding` associação.</span><span class="sxs-lookup"><span data-stu-id="310ec-121">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="310ec-122">Para determinado tipo e da configuração de aplicativo, as cadeias de caracteres de moniker de exemplo a seguir são usadas.</span><span class="sxs-lookup"><span data-stu-id="310ec-122">For the given type and application configuration, the following example moniker strings are used.</span></span>  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     <span data-ttu-id="310ec-123">Você pode usar qualquer uma dessas cadeias de caracteres de identificador de origem de dentro de um aplicativo Visual Basic 6.0, depois de adicionar uma referência ao assembly que contém o `IMathService` tipos, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="310ec-123">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     <span data-ttu-id="310ec-124">Neste exemplo, a definição para a configuração de associação `Binding1` é armazenado em um arquivo de configuração nomeada adequadamente para o aplicativo de cliente, como vb6appname.exe.config.</span><span class="sxs-lookup"><span data-stu-id="310ec-124">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as vb6appname.exe.config.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="310ec-125">Você pode usar um código semelhante em um C++, c# ou qualquer outro aplicativo de linguagem .NET.</span><span class="sxs-lookup"><span data-stu-id="310ec-125">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="310ec-126">: Se o moniker está mal formado ou se o serviço está indisponível, a chamada para `GetObject` retornará um erro de "Sintaxe inválida".</span><span class="sxs-lookup"><span data-stu-id="310ec-126">: If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="310ec-127">Se você receber esse erro, verifique se você estiver usando o identificador de origem está correto e o serviço está disponível.</span><span class="sxs-lookup"><span data-stu-id="310ec-127">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
     <span data-ttu-id="310ec-128">Embora este tópico se concentra no uso o moniker de serviço do código do VB 6.0, você pode usar um moniker de serviço de outros idiomas.</span><span class="sxs-lookup"><span data-stu-id="310ec-128">Although this topic focuses on using the service moniker from VB 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="310ec-129">Ao usar um moniker de C++ código de Svcutil.exe assembly gerado deve ser importado com "no_namespace named_guids raw_interfaces_only", conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="310ec-129">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     <span data-ttu-id="310ec-130">Isso modifica as definições de interface importado para que todos os métodos retornam um `HResult`.</span><span class="sxs-lookup"><span data-stu-id="310ec-130">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="310ec-131">Outro valores de retorno é convertido em parâmetros de saída.</span><span class="sxs-lookup"><span data-stu-id="310ec-131">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="310ec-132">A execução geral dos métodos permanece o mesmo.</span><span class="sxs-lookup"><span data-stu-id="310ec-132">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="310ec-133">Isso permite que você determine a causa de uma exceção ao chamar um método no proxy.</span><span class="sxs-lookup"><span data-stu-id="310ec-133">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="310ec-134">Essa funcionalidade só está disponível a partir do código C++.</span><span class="sxs-lookup"><span data-stu-id="310ec-134">This functionality is only available from C++ code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="310ec-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="310ec-135">See also</span></span>

- [<span data-ttu-id="310ec-136">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="310ec-136">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
