---
title: Como melhorar o tempo de inicialização dos aplicativos do cliente WCF usando o XmlSerializer
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: 6f61c57998cfc21b66f278a1a2381407ec2c39ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500123"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Como melhorar o tempo de inicialização dos aplicativos do cliente WCF usando o XmlSerializer
Os serviços e os aplicativos cliente que usam tipos de dados que são serializados usando <xref:System.Xml.Serialization.XmlSerializer> geram e compilam o código de serialização para esses tipos de dados em tempo de execução, o que pode levar a um desempenho de inicialização lento.  
  
> [!NOTE]
>  O código de serialização pré-gerado somente pode ser usado em aplicativos cliente e não em serviços.  
  
 O [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pode melhorar o desempenho de inicialização para esses aplicativos por meio da geração de código de serialização necessários dos assemblies compilados para o aplicativo. Svcutil.exe gera o código de serialização para todos os tipos de dados usados em contratos de serviço no assembly compilado do aplicativo que pode ser serializado usando o <xref:System.Xml.Serialization.XmlSerializer>. Contratos de serviço e operação que usam o <xref:System.Xml.Serialization.XmlSerializer> são marcados com o <xref:System.ServiceModel.XmlSerializerFormatAttribute>.  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>Para gerar o código de serialização de XmlSerializer  
  
1.  Compile seu código de serviço ou cliente em um ou mais assemblies.  
  
2.  Abra um prompt de comando do SDK.  
  
3.  No prompt de comando, inicie a ferramenta Svcutil.exe usando o seguinte formato.  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     O `assemblyPath` argumento especifica o caminho para um assembly que contém os tipos de contrato de serviço. Svcutil.exe gera o código de serialização para todos os tipos de dados usados em contratos de serviço no assembly compilado do aplicativo que pode ser serializado usando o <xref:System.Xml.Serialization.XmlSerializer>.  
  
     Svcutil.exe só pode gerar o código de serialização do c#. Um arquivo de código fonte é gerado para cada assembly de entrada. Não é possível usar o **/idioma** switch para alterar o idioma do código gerado.  
  
     Para especificar o caminho para assemblies dependentes, use o **/Reference** opção.  
  
4.  Verifique o código de serialização gerado disponíveis para seu aplicativo usando uma das seguintes opções:  
  
    1.  Compilar o código de serialização gerado em um assembly separado com o nome [*assembly original*]. XmlSerializers.dll (por exemplo, MyApp.XmlSerializers.dll). Seu aplicativo deve ser capaz de carregar o assembly, que deve ser assinado com a mesma chave do assembly original. Se você recompile o assembly original, você deve gerar novamente o assembly de serialização.  
  
    2.  Compilar o código de serialização gerado em um assembly separado e usar o <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> no contrato de serviço que usa o <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Definir o <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> propriedades para apontar para o assembly de serialização compilados.  
  
    3.  Compile o código de serialização gerado no seu assembly de aplicativo e adicione o <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> ao contrato de serviço que usa o <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Não defina o <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> propriedades. O assembly de serialização padrão é considerado o assembly atual.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Para gerar o código de serialização de XmlSerializer no Visual Studio  
  
1.  Crie o serviço do WCF e o cliente projetos no Visual Studio. Em seguida, adicione uma referência de serviço para o projeto de cliente.  
  
2.  Adicionar uma <xref:System.ServiceModel.XmlSerializerFormatAttribute> ao contrato de serviço a *reference.cs* arquivo no projeto de aplicativo cliente em **serviceReference** -> **svcmap** . Observe que você precisa mostrar todos os arquivos em **Solution Explorer** para ver esses arquivos.  
  
3.  Compile o aplicativo cliente.  
  
4.  Use o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para criar um serializador pré-gerado *. CS* arquivo usando o comando:  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     O argumento assemblyPath Especifica o caminho para o assembly de cliente do WCF.  
  
     Como:  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     O *WCFClient.XmlSerializers.dll.cs* arquivo será gerado.  
  
5.  Compile o assembly de serialização gerado previamente.  
  
     Com base no exemplo na etapa anterior, o comando de compilação seria o seguinte:  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Certifique-se de gerado *WCFClient.XmlSerializers.dll* está no mesmo diretório que o aplicativo cliente, que é *WCFClient.exe* nesse caso.  
  
6.  Execute o aplicativo cliente como de costume. O assembly de serialização gerado será usado.  
  
## <a name="example"></a>Exemplo  
 O comando a seguir gera os tipos de serialização para `XmlSerializer` tipos de contratos de qualquer serviço do uso de assembly.  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>Consulte também  
 [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
