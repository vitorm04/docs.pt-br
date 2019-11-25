---
title: Como registrar e configurar um Moniker de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: 47e11ff2bc5b1c3eca152ba1fa429b5785c2f01b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976119"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="f1be7-102">Como registrar e configurar um Moniker de serviço</span><span class="sxs-lookup"><span data-stu-id="f1be7-102">How to: Register and Configure a Service Moniker</span></span>
<span data-ttu-id="f1be7-103">Antes de usar o moniker do serviço Windows Communication Foundation (WCF) em um aplicativo com com um contrato tipado, você deve registrar os tipos atribuídos necessários com com e configurar o aplicativo COM e o moniker com a associação necessária configuração.</span><span class="sxs-lookup"><span data-stu-id="f1be7-103">Before using the Windows Communication Foundation (WCF) service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
### <a name="to-register-the-required-attributed-types-with-com"></a><span data-ttu-id="f1be7-104">Para registrar os tipos atribuídos necessários com com</span><span class="sxs-lookup"><span data-stu-id="f1be7-104">To register the required attributed types with COM</span></span>  
  
1. <span data-ttu-id="f1be7-105">Use a ferramenta [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para recuperar o contrato de metadados do serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="f1be7-105">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the WCF service.</span></span> <span data-ttu-id="f1be7-106">Isso gera o código-fonte para um assembly de cliente WCF e um arquivo de configuração de aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="f1be7-106">This generates the source code for a WCF client assembly and a client application configuration file.</span></span>  
  
2. <span data-ttu-id="f1be7-107">Verifique se os tipos no assembly estão marcados como `ComVisible`.</span><span class="sxs-lookup"><span data-stu-id="f1be7-107">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="f1be7-108">Para fazer isso, adicione o seguinte atributo ao arquivo AssemblyInfo.cs em seu projeto do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f1be7-108">To do so, add the following attribute to the AssemblyInfo.cs file in your Visual Studio project.</span></span>  
  
    ```csharp
    [assembly: ComVisible(true)]  
    ```  
  
3. <span data-ttu-id="f1be7-109">Compile o cliente WCF gerenciado como um assembly de nome forte.</span><span class="sxs-lookup"><span data-stu-id="f1be7-109">Compile the managed WCF client as a strong-named assembly.</span></span> <span data-ttu-id="f1be7-110">Isso requer a assinatura com um par de chaves de criptografia.</span><span class="sxs-lookup"><span data-stu-id="f1be7-110">This requires signing with a cryptographic key pair.</span></span> <span data-ttu-id="f1be7-111">Para obter mais informações, consulte [assinando um assembly com um nome forte](https://go.microsoft.com/fwlink/?LinkId=94874) no guia do desenvolvedor do .net.</span><span class="sxs-lookup"><span data-stu-id="f1be7-111">For more information, see [Signing an Assembly with a Strong Name](https://go.microsoft.com/fwlink/?LinkId=94874) in the .NET Developer's Guide.</span></span>  
  
4. <span data-ttu-id="f1be7-112">Use a ferramenta de registro do assembly (regasm. exe) com a opção `/tlb` para registrar os tipos no assembly com com.</span><span class="sxs-lookup"><span data-stu-id="f1be7-112">Use the Assembly Registration (Regasm.exe) tool with the `/tlb` option to register the types in the assembly with COM.</span></span>  
  
5. <span data-ttu-id="f1be7-113">Use a ferramenta cache de assembly global (Gacutil. exe) para adicionar o assembly ao cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="f1be7-113">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f1be7-114">Assinar o assembly e adicioná-lo ao cache de assembly global são etapas opcionais, mas eles podem simplificar o processo de carregamento do assembly a partir do local correto em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f1be7-114">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="f1be7-115">Para configurar o aplicativo COM e o moniker com a configuração de associação necessária</span><span class="sxs-lookup"><span data-stu-id="f1be7-115">To configure the COM application and the moniker with the required binding configuration</span></span>  
  
- <span data-ttu-id="f1be7-116">Coloque as definições de associação (geradas pela [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) no arquivo de configuração do aplicativo cliente gerado) no arquivo de configuração do aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="f1be7-116">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="f1be7-117">Por exemplo, para um executável Visual Basic 6,0 chamado CallCenterClient. exe, a configuração deve ser colocada em um arquivo chamado CallCenterConfig. exe. config no mesmo diretório que o executável.</span><span class="sxs-lookup"><span data-stu-id="f1be7-117">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="f1be7-118">O aplicativo cliente agora pode usar o moniker.</span><span class="sxs-lookup"><span data-stu-id="f1be7-118">The client application can now use the moniker.</span></span> <span data-ttu-id="f1be7-119">Observe que a configuração de associação não é necessária se estiver usando um dos tipos de associação padrão fornecidos pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="f1be7-119">Note that the binding configuration is not required if using one of the standard binding types provided by WCF.</span></span>  
  
     <span data-ttu-id="f1be7-120">O tipo a seguir é registrado.</span><span class="sxs-lookup"><span data-stu-id="f1be7-120">The following type is registered.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     <span data-ttu-id="f1be7-121">O aplicativo é exposto usando uma associação de `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="f1be7-121">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="f1be7-122">Para o tipo e a configuração de aplicativo fornecidos, as seguintes cadeias de caracteres de moniker de exemplo são usadas.</span><span class="sxs-lookup"><span data-stu-id="f1be7-122">For the given type and application configuration, the following example moniker strings are used.</span></span>  
  
    ``` 
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ``` 
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     <span data-ttu-id="f1be7-123">Você pode usar qualquer uma dessas cadeias de caracteres de moniker de dentro de um aplicativo Visual Basic 6,0, depois de adicionar uma referência ao assembly que contém os tipos de `IMathService`, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f1be7-123">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>  
  
    ```vb
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     <span data-ttu-id="f1be7-124">Neste exemplo, a definição para o `Binding1` de configuração de associação é armazenada em um arquivo de configuração nomeado adequadamente para o aplicativo cliente, como vb6appname. exe. config.</span><span class="sxs-lookup"><span data-stu-id="f1be7-124">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as vb6appname.exe.config.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f1be7-125">Você pode usar código semelhante em um C#, um C++ou qualquer outro aplicativo de linguagem .net.</span><span class="sxs-lookup"><span data-stu-id="f1be7-125">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f1be7-126">: Se o moniker estiver malformado ou se o serviço estiver indisponível, a chamada para `GetObject` retornará um erro de "sintaxe inválida".</span><span class="sxs-lookup"><span data-stu-id="f1be7-126">: If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="f1be7-127">Se você receber esse erro, verifique se o moniker que você está usando está correto e se o serviço está disponível.</span><span class="sxs-lookup"><span data-stu-id="f1be7-127">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
     <span data-ttu-id="f1be7-128">Embora este tópico se concentre no uso do moniker de serviço do código VB 6,0, você pode usar um moniker de serviço de outros idiomas.</span><span class="sxs-lookup"><span data-stu-id="f1be7-128">Although this topic focuses on using the service moniker from VB 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="f1be7-129">Ao usar um moniker do C++ código, o assembly gerado svcutil. exe deve ser importado com "no_namespace named_guids raw_interfaces_only", conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f1be7-129">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>  
  
    ```cpp
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     <span data-ttu-id="f1be7-130">Isso modifica as definições de interface importadas para que todos os métodos retornem um `HResult`.</span><span class="sxs-lookup"><span data-stu-id="f1be7-130">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="f1be7-131">Quaisquer outros valores de retorno são convertidos em parâmetros de saída.</span><span class="sxs-lookup"><span data-stu-id="f1be7-131">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="f1be7-132">A execução geral dos métodos permanece a mesma.</span><span class="sxs-lookup"><span data-stu-id="f1be7-132">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="f1be7-133">Isso permite que você determine a causa de uma exceção ao chamar um método no proxy.</span><span class="sxs-lookup"><span data-stu-id="f1be7-133">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="f1be7-134">Essa funcionalidade só está disponível no C++ código.</span><span class="sxs-lookup"><span data-stu-id="f1be7-134">This functionality is only available from C++ code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1be7-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1be7-135">See also</span></span>

- [<span data-ttu-id="f1be7-136">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="f1be7-136">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
