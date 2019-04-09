---
title: 'Como: melhorar o tempo de inicialização dos aplicativos do cliente WCF usando o XmlSerializer'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: dfc3dc8247a25442511d422192fea4f49bee5d92
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169800"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Como: melhorar o tempo de inicialização dos aplicativos do cliente WCF usando o XmlSerializer
Os serviços e os aplicativos cliente que usam tipos de dados que são serializados usando <xref:System.Xml.Serialization.XmlSerializer> geram e compilam o código de serialização para esses tipos de dados em tempo de execução, o que pode levar a um desempenho de inicialização lento.  
  
> [!NOTE]
>  O código de serialização pré-gerado somente pode ser usado em aplicativos cliente e não em serviços.  
  
 O [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pode melhorar o desempenho de inicialização para esses aplicativos, gerando o código de serialização necessários a partir de assemblies compilados para o aplicativo. Svcutil.exe gera o código de serialização para todos os tipos de dados usados em contratos de serviço no assembly compilado do aplicativo que pode ser serializado usando o <xref:System.Xml.Serialization.XmlSerializer>. Contratos de serviço e a operação que usam o <xref:System.Xml.Serialization.XmlSerializer> são marcados com o <xref:System.ServiceModel.XmlSerializerFormatAttribute>.  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>Para gerar o código de serialização de XmlSerializer  
  
1.  Compile seu código de serviço ou cliente em um ou mais assemblies.  
  
2.  Abra um prompt de comando do SDK.  
  
3.  No prompt de comando, inicie a ferramenta Svcutil.exe usando o seguinte formato.  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     O `assemblyPath` argumento especifica o caminho para um assembly que contém os tipos de contrato de serviço. Svcutil.exe gera o código de serialização para todos os tipos de dados usados em contratos de serviço no assembly compilado do aplicativo que pode ser serializado usando o <xref:System.Xml.Serialization.XmlSerializer>.  
  
     Svcutil.exe só podem gerar C# código de serialização. Um arquivo de código-fonte é gerado para cada assembly de entrada. Não é possível usar o **/idioma** switch para alterar o idioma do código gerado.  
  
     Para especificar o caminho para assemblies dependentes, use o **/Reference** opção.  
  
4.  Verifique o código de serialização gerado disponíveis para seu aplicativo usando uma das seguintes opções:  
  
    1.  Compilar o código de serialização gerado em um assembly separado com o nome [*assembly original*]. XmlSerializers (por exemplo, XmlSerializers). Seu aplicativo deve ser capaz de carregar o assembly, que deve ser assinado com a mesma chave que o assembly original. Se você recompilar o assembly original, você deve gerar novamente o assembly de serialização.  
  
    2.  Compilar o código de serialização gerado em um assembly separado e usar o <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> no contrato de serviço que usa o <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Defina as <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> propriedades para apontar para o assembly de serialização compilados.  
  
    3.  Compilar o código de serialização gerado para o seu assembly de aplicativo e adicione a <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> ao contrato de serviço que usa o <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Não defina a <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> propriedades. O assembly de serialização padrão será considerado o assembly atual.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Para gerar o código de serialização de XmlSerializer no Visual Studio  
  
1.  Crie o serviço do WCF e o cliente projetos no Visual Studio. Em seguida, adicione uma referência de serviço ao projeto cliente.  
  
2.  Adicionar um <xref:System.ServiceModel.XmlSerializerFormatAttribute> ao contrato de serviço na *reference.cs* arquivo no projeto de aplicativo do cliente sob **serviceReference** -> **svcmap** . Observe que você precisa mostrar todos os arquivos no **Gerenciador de soluções** para ver esses arquivos.  
  
3.  Compile o aplicativo cliente.  
  
4.  Use o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para criar um serializador pré-gerado *CS* arquivo usando o comando:  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     O argumento assemblyPath Especifica o caminho para o assembly de cliente do WCF.  
  
     Como:  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     O *WCFClient.XmlSerializers.dll.cs* arquivo será gerado.  
  
5.  Compile o assembly de serialização pré-gerado.  
  
     Com base no exemplo na etapa anterior, o comando de compilação seria o seguinte:  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Verifique se o gerado *WCFClient.XmlSerializers.dll* está no mesmo diretório que o aplicativo cliente, que está *WCFClient.exe* nesse caso.  
  
6.  Execute o aplicativo cliente como de costume. O assembly de serialização pré-gerado será usado.  
  
## <a name="example"></a>Exemplo  
 O comando a seguir gera tipos de serialização para `XmlSerializer` tipos de contratos de qualquer serviço o uso do assembly.  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>Consulte também

- [Ferramenta Utilitário de Metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
