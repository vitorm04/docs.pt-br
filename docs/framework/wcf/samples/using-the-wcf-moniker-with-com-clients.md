---
title: Usando o WCF Moniker com clientes COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: d4d812c59a504f365eb3ad63ddd45ba5a66296e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183228"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a>Usando o WCF Moniker com clientes COM
Esta amostra demonstra como usar o apelido de serviço da Windows Communication Foundation (WCF) para integrar serviços web em ambientes de desenvolvimento baseados em COM, como o Microsoft Office Visual Basic for Applications (Office VBA) ou o Visual Basic 6.0. Esta amostra consiste em um cliente Windows Script Host (.vbs), uma biblioteca de clientes de suporte (.dll) e uma biblioteca de serviços (.dll) hospedada pelo Internet Information Services (IIS). O serviço é um serviço de calculadora e o cliente COM chama operações matemáticas — Adicionar, Subtrair, Multiplicar e Dividir — no serviço. A atividade do cliente é visível nas janelas da caixa de mensagens.  
  
> [!NOTE]
> Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 O serviço implementa um `ICalculator` contrato definido como mostrado no exemplo de código a seguir.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 A amostra demonstra as três abordagens alternativas para o uso do apelido:  
  
- Contrato digitado – O contrato é registrado como um tipo visível COM no computador do cliente.  
  
- Contrato WSDL – O contrato é fornecido a forma de um documento WSDL.  
  
- Contrato de Troca de Metadados – O contrato é recuperado em tempo de execução a partir de um ponto final da Metadata Exchange (MEX).  
  
## <a name="typed-contract"></a>Contrato Digitado  
 Para utilizar o apelido com uso de contrato digitado, os tipos devidamente atribuídos ao contrato de serviço devem ser registrados no COM. Primeiro, um cliente deve ser gerado usando a [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Execute o seguinte comando a partir de um prompt de comando no diretório do cliente para gerar o proxy digitado.  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 Esta classe deve ser incluída em um projeto e o projeto deve ser configurado para gerar uma montagem assinada e visível com COM quando compilado. O seguinte atributo deve ser incluído no arquivo AssemblyInfo.cs.  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 Após a construção do projeto, registre `regasm` os tipos visíveis com usando como mostrado no exemplo a seguir.  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 A montagem criada deve ser adicionada ao Cache de Montagem Global. Embora não seja estritamente necessário, isso simplifica o processo de localização do conjunto em tempo de execução. O comando a seguir adiciona a montagem ao Cache de Montagem Global.  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> O apelido de serviço requer apenas o registro do tipo e não usa o proxy para se comunicar com o serviço.  
  
 O aplicativo cliente ComCalcClient.vbs usa a `GetObject` função para construir um proxy para o serviço, usando a sintaxe de apelido de serviço para especificar o endereço, a vinculação e o contrato do serviço.  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 Os parâmetros utilizados pelo apelido especificam:  
  
- O endereço do ponto de extremidade de serviço.  
  
- A vinculação que o cliente deve usar para se conectar com esse ponto final. Neste caso, o wsHttpBinding definido pelo sistema é usado, embora as vinculações personalizadas possam ser definidas em arquivos de configuração do cliente. Para uso com o Windows Script Host, a vinculação personalizada é definida em um arquivo Cscript.exe.config no mesmo diretório que Cscript.exe.  
  
- O tipo de contrato que é suportado no ponto final. Este é o tipo que foi gerado e registrado acima. Como o script Visual Basic não fornece um ambiente COM fortemente digitado, um identificador para o contrato deve ser especificado. Este GUID `interfaceID` é o de CalcProxy.tlb, que pode ser visualizado usando ferramentas COM como o OLE/COM Object Viewer (OleView.exe). Para ambientes fortemente digitados, como o Office VBA ou o Visual Basic 6.0, adicionar uma referência explícita à biblioteca do tipo e, em seguida, declarar o tipo do objeto proxy pode ser usado no lugar do parâmetro do contrato. Isso também fornece suporte ao IntelliSense durante o desenvolvimento de aplicativos clientes.  
  
 Tendo construído a instância proxy com o apelido de serviço, o aplicativo cliente pode chamar métodos no proxy, o que resulta na infra-estrutura de apelido de serviço chamando as operações de serviço correspondentes.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Quando você executa a amostra, a resposta de operação é exibida em uma janela de caixa de mensagens do Windows Script Host. Isso demonstra um cliente COM fazendo chamadas COM usando o apelido digitado para se comunicar com um serviço WCF. Apesar do uso do COM no aplicativo do cliente, a comunicação com o serviço consiste apenas em chamadas de serviço web.  
  
## <a name="wsdl-contract"></a>Contrato WSDL  
 Para usar o apelido com um contrato WSDL, nenhum registro de biblioteca de clientes é necessário, mas o contrato WSDL para o serviço deve ser recuperado através de um mecanismo fora de banda, como usar um navegador para acessar o ponto final do WSDL para o serviço. O apelido pode então acessar esse contrato na hora da execução.  
  
 O aplicativo cliente ComCalcClient.vbs usa o `FileSystemObject` para acessar o arquivo WSDL salvo localmente e, em seguida, novamente usa a `GetObject` função para construir um proxy para o serviço.  
  
```vbscript  
' Open the WSDL contract file and read it all into the wsdlContract string  
Const ForReading = 1  
Set objFSO = CreateObject("Scripting.FileSystemObject")  
Set objFile = objFSO.OpenTextFile("serviceWsdl.xml", ForReading)  
wsdlContract = objFile.ReadAll  
objFile.Close  
  
' Create a string for the service moniker including the content of the WSDL contract file  
wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
```  
  
 Os parâmetros utilizados pelo apelido especificam:  
  
- O endereço do ponto de extremidade de serviço.  
  
- A vinculação que o cliente deve usar para se conectar com esse ponto final e o namespace no qual essa vinculação é definida. Neste caso, `wsHttpBinding_ICalculator` o é usado.  
  
- O WSDL que define o contrato. Neste caso, esta é a string que foi lida a partir do arquivo serviceWsdl.xml.  
  
- O nome e o espaço do contrato. Esta identificação é necessária porque o WSDL pode conter mais de um contrato.  
  
    > [!NOTE]
    > Por padrão, os serviços WCF geram arquivos WSDL separados para cada namespace que o uso. Estes estão ligados ao uso da construção de importação WSDL. Como o apelido espera uma única definição de WSDL, o serviço deve usar um único namespace como demonstrado nesta amostra ou os arquivos separados devem ser mesclados manualmente.  
  
 Tendo construído a instância proxy com o apelido de serviço, o aplicativo cliente pode chamar métodos no proxy, o que resulta na infra-estrutura de apelido de serviço chamando as operações de serviço correspondentes.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Quando você executa a amostra, a resposta de operação é exibida em uma janela de caixa de mensagens do Windows Script Host. Isso demonstra um cliente COM fazendo chamadas COM usando o apelido com um contrato WSDL para se comunicar com um serviço WCF.  
  
## <a name="metadata-exchange-contract"></a>Contrato de Troca de Metadados  
 Para usar o apelido com um contrato MEX, como no contrato WSDL, não é necessário registro de cliente. O contrato para o serviço é recuperado no momento da execução através do uso interno do Metadata Exchange.  
  
 O aplicativo cliente ComCalcClient.vbs `GetObject` novamente usa a função para construir um proxy para o serviço.  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 Os parâmetros utilizados pelo apelido especificam:  
  
- O endereço do ponto final de troca de metadados do serviço.  
  
- O endereço do ponto de extremidade de serviço.  
  
- A vinculação que o cliente deve usar para se conectar com esse ponto final e o namespace no qual essa vinculação é definida. Neste caso, `wsHttpBinding_ICalculator` o é usado.  
  
- O nome e o espaço do contrato. Esta identificação é necessária porque o WSDL pode conter mais de um contrato.  
  
 Tendo construído a instância proxy com o apelido de serviço, o aplicativo cliente pode chamar métodos no proxy, o que resulta na infra-estrutura de apelido de serviço chamando as operações de serviço correspondentes.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Quando você executa a amostra, a resposta de operação é exibida em uma janela de caixa de mensagens do Windows Script Host. Isso demonstra um cliente COM fazendo chamadas COM usando o apelido com um contrato MEX para se comunicar com um serviço WCF.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Para configurar e construir a amostra  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. A partir de um prompt de comando de desenvolvedor para o Visual Studio, abra a pasta \client\bin, na pasta específica do idioma.  
  
    > [!NOTE]
    > Se você estiver usando o Windows Vista, Windows Server 2008, Windows 7 ou Windows Server 2008 R2, certifique-se de executar o prompt de comando com privilégios de administrador.  
  
4. Digite `tlbexp.exe client.dll /out:CalcProxy.tlb` para exportar o dll para um arquivo tlb. Um "Aviso de exportador de biblioteca tipo" é esperado, mas não é um problema porque o tipo genérico não é necessário.  
  
5. Digite `regasm.exe /tlb:CalcProxy.tlb client.dll` para registrar os tipos com COM. Um "Aviso de exportador de biblioteca tipo" é esperado, mas não é um problema porque o tipo genérico não é necessário.  
  
6. Digite `gacutil.exe /i client.dll` para adicionar o conjunto ao Cache de Montagem Global.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar a amostra no mesmo computador  
  
1. Teste que você pode acessar o serviço usando um `http://localhost/servicemodelsamples/service.svc`navegador digitando no seguinte endereço: . Uma página de confirmação deve ser exibida em resposta.  
  
2. Execute ComCalcClient.vbs a partir de \client, a partir da pasta específica do idioma. A atividade do cliente é exibida nas janelas da caixa de mensagens.  
  
3. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Para executar a amostra através de computadores  
  
1. No computador de serviço, crie um diretório virtual chamado ServiceModelSamples. O script Setupvroot.bat incluído na amostra pode ser usado para criar o diretório de disco e o diretório virtual.  
  
2. Copie os arquivos do programa de serviço de %SystemDrive%\Inetpub\wwwroot\servicemodelsamples para o diretório virtual ServiceModelSamples no computador de serviço. Certifique-se de incluir os arquivos no diretório \bin.  
  
3. Copie o arquivo de script cliente da pasta \client, a pasta específica do idioma, para o computador cliente.  
  
4. No arquivo de script, altere o valor de endereço da definição de ponto final para corresponder ao novo endereço do seu serviço. Substitua quaisquer referências a "localhost" por um nome de domínio totalmente qualificado no endereço.  
  
5. Copie o arquivo WSDL para o computador cliente. No arquivo WSDL, serviceWsdl.xml, substitua quaisquer referências a "localhost" por um nome de domínio totalmente qualificado no endereço.  
  
6. Copie a biblioteca Client.dll da pasta \client\bin, na pasta específica do idioma, para um diretório no computador cliente.  
  
7. A partir de um prompt de comando, navegue até o diretório de destino no computador cliente. Se estiver usando o Windows Vista ou o Windows Server 2008, certifique-se de executar o prompt de comando como Administrador.  
  
8. Digite `tlbexp.exe client.dll /out:CalcProxy.tlb` para exportar o dll para um arquivo tlb. Um "Aviso de exportador de biblioteca tipo" é esperado, mas não é um problema porque o tipo genérico não é necessário.  
  
9. Digite `regasm.exe /tlb:CalcProxy.tlb client.dll` para registrar os tipos com COM. Certifique-se de que o caminho `regasm.exe` foi definido para a pasta que contém antes de executar o comando.  
  
10. Digite `gacutil.exe /i client.dll` para adicionar o conjunto ao Cache de Montagem Global. Certifique-se de que o caminho `gacutil.exe` foi definido para a pasta que contém antes de executar o comando.  
  
11. Teste que você pode acessar o serviço a partir do computador cliente usando um navegador.  
  
12. No computador cliente, inicie ComCalcClient.vbs.  
  
#### <a name="to-clean-up-after-the-sample"></a>Para limpar depois da amostra  
  
- Para efeitos de segurança, remova a definição de diretório virtual e as permissões concedidas nas etapas de configuração quando terminar com as amostras.  
