---
title: 'Como: usar Svcutil.exe para exportar metadados de código de serviço compilado'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: 2d1b70931fe70dfd605e182d4b23a151bc8130a3
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991174"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a><span data-ttu-id="9b8ba-102">Como: usar Svcutil.exe para exportar metadados de código de serviço compilado</span><span class="sxs-lookup"><span data-stu-id="9b8ba-102">How to: Use Svcutil.exe to Export Metadata from Compiled Service Code</span></span>
<span data-ttu-id="9b8ba-103">Svcutil. exe pode exportar metadados para serviços, contratos e tipos de dados em assemblies compilados, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9b8ba-103">Svcutil.exe can export metadata for services, contracts, and data types in compiled assemblies, as follows:</span></span>  
  
- <span data-ttu-id="9b8ba-104">Para exportar metadados para todos os contratos de serviço compilados para um conjunto de assemblies usando svcutil. exe, especifique os assemblies como parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-104">To export metadata for all compiled service contracts for a set of assemblies using Svcutil.exe, specify the assemblies as input parameters.</span></span> <span data-ttu-id="9b8ba-105">Esse é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-105">This is the default behavior.</span></span>  
  
- <span data-ttu-id="9b8ba-106">Para exportar metadados para um serviço compilado usando svcutil. exe, especifique o assembly de serviço ou assemblies como parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-106">To export metadata for a compiled service using Svcutil.exe, specify the service assembly or assemblies as input parameters.</span></span> <span data-ttu-id="9b8ba-107">Você deve usar a `/serviceName` opção para indicar o nome da configuração do serviço que deseja exportar.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-107">You must use the `/serviceName` option to indicate the configuration name of the service you want to export.</span></span> <span data-ttu-id="9b8ba-108">Svcutil. exe carrega automaticamente o arquivo de configuração para o assembly executável especificado.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-108">Svcutil.exe automatically loads the configuration file for the specified executable assembly.</span></span>  
  
- <span data-ttu-id="9b8ba-109">Para exportar todos os tipos de contrato de dados dentro de um conjunto de `/dataContractOnly` assemblies, use a opção.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-109">To export all data contract types within a set of assemblies, use the `/dataContractOnly` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b8ba-110">Use a `/reference` opção para especificar os caminhos de arquivo para quaisquer assemblies dependentes.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-110">Use the `/reference` option to specify the file paths to any dependent assemblies.</span></span>  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a><span data-ttu-id="9b8ba-111">Para exportar metadados para contratos de serviço compilados</span><span class="sxs-lookup"><span data-stu-id="9b8ba-111">To export metadata for compiled service contracts</span></span>  
  
1. <span data-ttu-id="9b8ba-112">Compile as implementações do contrato de serviço em uma ou mais bibliotecas de classe. 1</span><span class="sxs-lookup"><span data-stu-id="9b8ba-112">Compile your service contract implementations into one or more class libraries.1</span></span>  
  
2. <span data-ttu-id="9b8ba-113">Execute svcutil. exe nos assemblies compilados.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-113">Run Svcutil.exe on the compiled assemblies.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9b8ba-114">Talvez seja necessário usar a `/reference` opção para especificar o caminho do arquivo para quaisquer assemblies dependentes.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-114">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```console
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a><span data-ttu-id="9b8ba-115">Para exportar metadados para um serviço compilado</span><span class="sxs-lookup"><span data-stu-id="9b8ba-115">To export metadata for a compiled service</span></span>  
  
1. <span data-ttu-id="9b8ba-116">Compile sua implementação de serviço em um assembly executável.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-116">Compile your service implementation into an executable assembly.</span></span>  
  
2. <span data-ttu-id="9b8ba-117">Crie um arquivo de configuração para o executável do serviço e adicione uma configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-117">Create a configuration file for your service executable and add a service configuration.</span></span>  
  
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
  
3. <span data-ttu-id="9b8ba-118">Execute svcutil. exe no executável do serviço compilado usando a `/serviceName` opção para especificar o nome da configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-118">Run Svcutil.exe on the compiled service executable using the `/serviceName` switch to specify the configuration name of the service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9b8ba-119">Talvez seja necessário usar a `/reference` opção para especificar o caminho do arquivo para quaisquer assemblies dependentes.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-119">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```console  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a><span data-ttu-id="9b8ba-120">Para exportar metadados para contratos de dados compilados</span><span class="sxs-lookup"><span data-stu-id="9b8ba-120">To export metadata for compiled data contracts</span></span>  
  
1. <span data-ttu-id="9b8ba-121">Compile suas implementações de contrato de dados em uma ou mais bibliotecas de classes.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-121">Compile your data contract implementations into one or more class libraries.</span></span>  
  
2. <span data-ttu-id="9b8ba-122">Execute svcutil. exe nos assemblies compilados usando a `/dataContract` opção para especificar que somente os metadados para contratos de dados devem ser gerados.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-122">Run Svcutil.exe on the compiled assemblies using the `/dataContract` switch to specify that only metadata for data contracts should be generated.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9b8ba-123">Talvez seja necessário usar a `/reference` opção para especificar o caminho do arquivo para quaisquer assemblies dependentes.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-123">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```console  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a><span data-ttu-id="9b8ba-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b8ba-124">Example</span></span>  
 <span data-ttu-id="9b8ba-125">O exemplo a seguir demonstra como gerar metadados para uma configuração e implementação de serviço simples.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-125">The following example demonstrates how to generate metadata for a simple service implementation and configuration.</span></span>  
  
 <span data-ttu-id="9b8ba-126">Para exportar metadados para o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-126">To export metadata for the service contract.</span></span>  
  
```console  
svcutil.exe Contracts.dll  
```  
  
 <span data-ttu-id="9b8ba-127">Para exportar metadados para os contratos de dados.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-127">To export metadata for the data contracts.</span></span>  
  
```console  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 <span data-ttu-id="9b8ba-128">Para exportar metadados para a implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-128">To export metadata for the service implementation.</span></span>  
  
```console  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 <span data-ttu-id="9b8ba-129">O `<path>` é o caminho para Contracts. dll.</span><span class="sxs-lookup"><span data-stu-id="9b8ba-129">The `<path>` is the path to Contracts.dll.</span></span>  
  
```csharp
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
```

```csharp
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
```

```xml  
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
  
## <a name="see-also"></a><span data-ttu-id="9b8ba-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b8ba-130">See also</span></span>

- [<span data-ttu-id="9b8ba-131">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="9b8ba-131">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="9b8ba-132">Exportando e importando metadados</span><span class="sxs-lookup"><span data-stu-id="9b8ba-132">Exporting and Importing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
