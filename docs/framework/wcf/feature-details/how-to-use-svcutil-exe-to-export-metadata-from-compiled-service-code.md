---
title: 'Como: usar Svcutil.exe para exportar metadados de código de serviço compilado'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: 5b905b6943127d483e001749c263242550ab28ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047328"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a><span data-ttu-id="0fc6e-102">Como: usar Svcutil.exe para exportar metadados de código de serviço compilado</span><span class="sxs-lookup"><span data-stu-id="0fc6e-102">How to: Use Svcutil.exe to Export Metadata from Compiled Service Code</span></span>
<span data-ttu-id="0fc6e-103">Svcutil.exe pode exportar metadados para os serviços, contratos e tipos de dados em assemblies compilados, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0fc6e-103">Svcutil.exe can export metadata for services, contracts, and data types in compiled assemblies, as follows:</span></span>  
  
- <span data-ttu-id="0fc6e-104">Para exportar metadados para todos os compilado contratos de serviço para um conjunto de módulos (assemblies) usando Svcutil.exe, especifique os assemblies como parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-104">To export metadata for all compiled service contracts for a set of assemblies using Svcutil.exe, specify the assemblies as input parameters.</span></span> <span data-ttu-id="0fc6e-105">Este é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-105">This is the default behavior.</span></span>  
  
- <span data-ttu-id="0fc6e-106">Para exportar metadados para um serviço compilado usando Svcutil.exe, especifique o assembly de serviço ou assemblies como parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-106">To export metadata for a compiled service using Svcutil.exe, specify the service assembly or assemblies as input parameters.</span></span> <span data-ttu-id="0fc6e-107">Você deve usar o `/serviceName` opção para indicar o nome da configuração do serviço que você deseja exportar.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-107">You must use the `/serviceName` option to indicate the configuration name of the service you want to export.</span></span> <span data-ttu-id="0fc6e-108">Svcutil.exe carregará automaticamente o arquivo de configuração para o assembly executável especificado.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-108">Svcutil.exe automatically loads the configuration file for the specified executable assembly.</span></span>  
  
- <span data-ttu-id="0fc6e-109">Para exportar todos os tipos de contrato de dados em um conjunto de módulos (assemblies), use o `/dataContractOnly` opção.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-109">To export all data contract types within a set of assemblies, use the `/dataContractOnly` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fc6e-110">Use o `/reference` opção para especificar os caminhos de arquivo para todos os assemblies dependentes.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-110">Use the `/reference` option to specify the file paths to any dependent assemblies.</span></span>  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a><span data-ttu-id="0fc6e-111">Para exportar metadados para contratos de serviço compilado</span><span class="sxs-lookup"><span data-stu-id="0fc6e-111">To export metadata for compiled service contracts</span></span>  
  
1. <span data-ttu-id="0fc6e-112">Compile suas implementações de contrato de serviço em um ou mais libraries.1 de classe</span><span class="sxs-lookup"><span data-stu-id="0fc6e-112">Compile your service contract implementations into one or more class libraries.1</span></span>  
  
2. <span data-ttu-id="0fc6e-113">Execute Svcutil.exe em assemblies compilados.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-113">Run Svcutil.exe on the compiled assemblies.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0fc6e-114">Você talvez precise usar o `/reference` para especificar o caminho do arquivo para todos os assemblies dependentes.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-114">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a><span data-ttu-id="0fc6e-115">Para exportar metadados para um serviço compilado</span><span class="sxs-lookup"><span data-stu-id="0fc6e-115">To export metadata for a compiled service</span></span>  
  
1. <span data-ttu-id="0fc6e-116">Compile sua implementação de serviço em um assembly executável.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-116">Compile your service implementation into an executable assembly.</span></span>  
  
2. <span data-ttu-id="0fc6e-117">Crie um arquivo de configuração para o executável do serviço e adicione uma configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-117">Create a configuration file for your service executable and add a service configuration.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="MyService" >  
            <endpoint address="finder" contract="IPeopleFinder" binding="wsHttpBinding" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
3. <span data-ttu-id="0fc6e-118">Execute Svcutil.exe no serviço compilado executável usando o `/serviceName` para especificar o nome da configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-118">Run Svcutil.exe on the compiled service executable using the `/serviceName` switch to specify the configuration name of the service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0fc6e-119">Você talvez precise usar o `/reference` para especificar o caminho do arquivo para todos os assemblies dependentes.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-119">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a><span data-ttu-id="0fc6e-120">Para exportar metadados para contratos de dados compilado</span><span class="sxs-lookup"><span data-stu-id="0fc6e-120">To export metadata for compiled data contracts</span></span>  
  
1. <span data-ttu-id="0fc6e-121">Compile suas implementações de contrato de dados em uma ou mais bibliotecas de classe.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-121">Compile your data contract implementations into one or more class libraries.</span></span>  
  
2. <span data-ttu-id="0fc6e-122">Executar Svcutil.exe em assemblies compilados usando o `/dataContract` para especificar que apenas os metadados para contratos de dados devem ser gerados.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-122">Run Svcutil.exe on the compiled assemblies using the `/dataContract` switch to specify that only metadata for data contracts should be generated.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0fc6e-123">Você talvez precise usar o `/reference` para especificar o caminho do arquivo para todos os assemblies dependentes.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-123">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a><span data-ttu-id="0fc6e-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0fc6e-124">Example</span></span>  
 <span data-ttu-id="0fc6e-125">O exemplo a seguir demonstra como gerar metadados para uma implementação de serviço simples e a configuração.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-125">The following example demonstrates how to generate metadata for a simple service implementation and configuration.</span></span>  
  
 <span data-ttu-id="0fc6e-126">Para exportar metadados para o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-126">To export metadata for the service contract.</span></span>  
  
```  
svcutil.exe Contracts.dll  
```  
  
 <span data-ttu-id="0fc6e-127">Para exportar metadados para os contratos de dados.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-127">To export metadata for the data contracts.</span></span>  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 <span data-ttu-id="0fc6e-128">Para exportar metadados para a implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-128">To export metadata for the service implementation.</span></span>  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 <span data-ttu-id="0fc6e-129">O `<path>` é o caminho para Contracts.dll.</span><span class="sxs-lookup"><span data-stu-id="0fc6e-129">The `<path>` is the path to Contracts.dll.</span></span>  
  
```  
// The following service contract and data contracts are compiled into   
// Contracts.dll.  
[ServiceContract(ConfigurationName="IPeopleFinder")]  
public interface IPersonFinder  
{  
    [OperationContract]  
    Address GetAddress(Person s);  
}  
  
[DataContract]  
public class Person  
{  
    [DataMember]  
    public string firstName;  
    [DataMember]  
    public string lastName;  
    [DataMember]  
    public int age;  
}  
  
[DataContract]  
public class Address  
{  
    [DataMember]  
    public string city;  
    [DataMember]  
    public string state;  
    [DataMember]  
    public string street;  
    [DataMember]  
    public int zipCode;  
    [DataMember]  
    public Person person;  
}  
  
// The following service implementation is compiled into Service.exe.     
// This service uses the contracts specified in Contracts.dll.  
[ServiceBehavior(ConfigurationName = "MyService")]  
public class MyService : IPersonFinder  
{  
    public Address GetAddress(Person person)  
    {  
        Address address = new Address();  
        address.person = person;  
        return address;  
    }  
}  
  
<!-- The following is the configuration file for Service.exe. -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="MyService">  
         <endpoint  address="finder"  
                    binding="basicHttpBinding"  
                    contract="IPeopleFinder"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fc6e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0fc6e-130">See also</span></span>

- [<span data-ttu-id="0fc6e-131">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="0fc6e-131">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="0fc6e-132">Exportando e importando metadados</span><span class="sxs-lookup"><span data-stu-id="0fc6e-132">Exporting and Importing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
