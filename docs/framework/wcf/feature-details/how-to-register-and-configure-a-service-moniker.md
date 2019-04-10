---
title: 'Como: registrar e configurar um moniker de serviço'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: dfac833cc7517af00d0264fc5d11fc83ae543569
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313574"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>Como: registrar e configurar um moniker de serviço
Antes de usar o moniker de serviço do Windows Communication Foundation (WCF) dentro de um aplicativo COM um contrato com tipo, você deve registrar os tipos de atributo necessários com e configurar o aplicativo COM e o identificador de origem com a ligação exigida configuração.  
  
### <a name="to-register-the-required-attributed-types-with-com"></a>Para registrar os tipos de atributo necessários COM  
  
1. Use o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta para recuperar o contrato de metadados do serviço WCF. Isso gera o código-fonte para um assembly de cliente do WCF e um arquivo de configuração de aplicativo do cliente.  
  
2. Certifique-se de que os tipos no assembly são marcados como `ComVisible`. Para fazer isso, adicione o seguinte atributo ao arquivo AssemblyInfo.cs no projeto do Visual Studio.  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3. Compile o cliente WCF gerenciado como um assembly de nome forte. Isso exige a assinar com um par de chaves criptográficas. Para obter mais informações, consulte [assinar um Assembly com um nome forte](https://go.microsoft.com/fwlink/?LinkId=94874) no guia do desenvolvedor do .NET.  
  
4. Use a ferramenta de registro do Assembly (Regasm.exe) com o `/tlb` opção registrar os tipos no assembly com COM.  
  
5. Use a ferramenta de Cache de Assembly Global (Gacutil.exe) para adicionar o assembly no cache de assembly global.  
  
    > [!NOTE]
    >  Assinar o assembly e adicioná-lo ao Cache de Assembly Global são etapas opcionais, mas elas podem simplificar o processo de carregar o assembly do local correto no tempo de execução.  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>Para configurar o aplicativo COM e o moniker com a configuração de associação necessários  
  
-   Coloque as definições de associação (gerado pelo [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) no arquivo de configuração do aplicativo cliente gerado) no arquivo de configuração do aplicativo cliente. Por exemplo, para um Visual Basic 6.0 executável denominado CallCenterClient.exe, a configuração deve ser colocada em um arquivo chamado CallCenterConfig.exe.config dentro do mesmo diretório que o executável. O aplicativo cliente agora pode usar o moniker. Observe que a configuração de associação não será necessária se usando um dos tipos fornecidos pelo WCF de associação padrão.  
  
     O tipo a seguir está registrado.  
  
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
  
     O aplicativo ficará exposto usando uma `wsHttpBinding` associação. Para determinado tipo e da configuração de aplicativo, as cadeias de caracteres de moniker de exemplo a seguir são usadas.  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     Você pode usar qualquer uma dessas cadeias de caracteres de identificador de origem de dentro de um aplicativo Visual Basic 6.0, depois de adicionar uma referência ao assembly que contém o `IMathService` tipos, conforme mostrado no código de exemplo a seguir.  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     Neste exemplo, a definição para a configuração de associação `Binding1` é armazenado em um arquivo de configuração nomeada adequadamente para o aplicativo de cliente, como vb6appname.exe.config.  
  
    > [!NOTE]
    >  Você pode usar um código semelhante em um C++, c# ou qualquer outro aplicativo de linguagem .NET.  
  
    > [!NOTE]
    >  : Se o moniker está mal formado ou se o serviço está indisponível, a chamada para `GetObject` retornará um erro de "Sintaxe inválida". Se você receber esse erro, verifique se você estiver usando o identificador de origem está correto e o serviço está disponível.  
  
     Embora este tópico se concentra no uso o moniker de serviço do código do VB 6.0, você pode usar um moniker de serviço de outros idiomas. Ao usar um moniker de C++ código de Svcutil.exe assembly gerado deve ser importado com "no_namespace named_guids raw_interfaces_only", conforme mostrado no código a seguir.  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     Isso modifica as definições de interface importado para que todos os métodos retornam um `HResult`. Outro valores de retorno é convertido em parâmetros de saída. A execução geral dos métodos permanece o mesmo. Isso permite que você determine a causa de uma exceção ao chamar um método no proxy. Essa funcionalidade só está disponível a partir do código C++.  
  
## <a name="see-also"></a>Consulte também

- [Ferramenta Utilitário de Metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
