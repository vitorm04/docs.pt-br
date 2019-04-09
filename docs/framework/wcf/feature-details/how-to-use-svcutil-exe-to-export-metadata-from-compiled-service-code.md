---
title: 'Como: usar Svcutil.exe para exportar metadados de código de serviço compilado'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: cb1cb03a078eeb273c69cc3c49b3ef2173c0a49c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084897"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>Como: usar Svcutil.exe para exportar metadados de código de serviço compilado
Svcutil.exe pode exportar metadados para os serviços, contratos e tipos de dados em assemblies compilados, da seguinte maneira:  
  
-   Para exportar metadados para todos os compilado contratos de serviço para um conjunto de módulos (assemblies) usando Svcutil.exe, especifique os assemblies como parâmetros de entrada. Este é o comportamento padrão.  
  
-   Para exportar metadados para um serviço compilado usando Svcutil.exe, especifique o assembly de serviço ou assemblies como parâmetros de entrada. Você deve usar o `/serviceName` opção para indicar o nome da configuração do serviço que você deseja exportar. Svcutil.exe carregará automaticamente o arquivo de configuração para o assembly executável especificado.  
  
-   Para exportar todos os tipos de contrato de dados em um conjunto de módulos (assemblies), use o `/dataContractOnly` opção.  
  
> [!NOTE]
>  Use o `/reference` opção para especificar os caminhos de arquivo para todos os assemblies dependentes.  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>Para exportar metadados para contratos de serviço compilado  
  
1.  Compile suas implementações de contrato de serviço em um ou mais libraries.1 de classe  
  
2.  Execute Svcutil.exe em assemblies compilados.  
  
    > [!NOTE]
    >  Você talvez precise usar o `/reference` para especificar o caminho do arquivo para todos os assemblies dependentes.  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a>Para exportar metadados para um serviço compilado  
  
1.  Compile sua implementação de serviço em um assembly executável.  
  
2.  Crie um arquivo de configuração para o executável do serviço e adicione uma configuração de serviço.  
  
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
  
3.  Execute Svcutil.exe no serviço compilado executável usando o `/serviceName` para especificar o nome da configuração do serviço.  
  
    > [!NOTE]
    >  Você talvez precise usar o `/reference` para especificar o caminho do arquivo para todos os assemblies dependentes.  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>Para exportar metadados para contratos de dados compilado  
  
1.  Compile suas implementações de contrato de dados em uma ou mais bibliotecas de classe.  
  
2.  Executar Svcutil.exe em assemblies compilados usando o `/dataContract` para especificar que apenas os metadados para contratos de dados devem ser gerados.  
  
    > [!NOTE]
    >  Você talvez precise usar o `/reference` para especificar o caminho do arquivo para todos os assemblies dependentes.  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como gerar metadados para uma implementação de serviço simples e a configuração.  
  
 Para exportar metadados para o contrato de serviço.  
  
```  
svcutil.exe Contracts.dll  
```  
  
 Para exportar metadados para os contratos de dados.  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 Para exportar metadados para a implementação do serviço.  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 O `<path>` é o caminho para Contracts.dll.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Ferramenta Utilitário de Metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Exportando e importando metadados](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
