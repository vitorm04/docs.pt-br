---
title: Usando o WCF Moniker com clientes COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 14907dd3df66478e8f84b7735a84dd500855448b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768378"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a>Usando o WCF Moniker com clientes COM
Este exemplo demonstra como usar o moniker de serviço do Windows Communication Foundation (WCF) para integrar serviços da Web em ambientes de desenvolvimento baseado em COM, como o Microsoft Office Visual Basic for Applications (VBA do Office) ou Visual Basic 6.0. Esse exemplo consiste em um cliente do Windows Script Host (. vbs), uma biblioteca de cliente com suporte (. dll) e uma biblioteca de serviço (. dll) hospedado pelo Internet Information Services (IIS). O serviço é um serviço de Calculadora e o cliente COM chama operações matemáticas — adicionar, subtrair, multiplicar e dividir — no serviço. Atividade do cliente está visível nas janelas de caixa de mensagem.  
  
> [!NOTE]
>  Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 O serviço implementa um `ICalculator` contrato definido conforme mostrado no exemplo de código a seguir.  
  
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
  
 O exemplo demonstra as três abordagens alternativas para usar o moniker:  
  
-   Contrato tipado – o contrato é registrado como um tipo visível de COM no computador cliente.  
  
-   Contrato WSDL – o contrato é fornecido na forma de um documento WSDL.  
  
-   Contrato de troca de metadados – o contrato é recuperado em tempo de execução de um ponto de extremidade de troca de metadados (MEX).  
  
## <a name="typed-contract"></a>Tipo de contrato  
 Para usar o moniker com um contrato com tipo de uso, tipos de atributo adequadamente para o contrato de serviço devem ser registrados com. Primeiro, um cliente deve ser gerado usando o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Execute o seguinte comando em um prompt de comando no diretório do cliente para gerar o proxy tipado.  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 Essa classe deve ser incluída em um projeto e o projeto deve ser configurado para gerar um visível em COM, assinado assembly quando compilado. O seguinte atributo deve ser incluído no arquivo AssemblyInfo.cs.  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 Depois de criar o projeto, registrar os tipos visível usando `regasm` conforme mostrado no exemplo a seguir.  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 O assembly que é criado deve ser adicionado ao Cache de Assembly Global. Embora não seja estritamente necessário, isso simplifica o processo de tempo de execução localizar o assembly. O comando a seguir adiciona o assembly no cache de Assembly Global.  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  O moniker de serviço requer somente o registro do tipo e não usa o proxy para se comunicar com o serviço.  
  
 Aplicativo de cliente ComCalcClient.vbs usa o `GetObject` função para construir um proxy para o serviço, usando a sintaxe de moniker de serviço para especificar o endereço, associação e de contrato para o serviço.  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 Especificam os parâmetros usados pelo moniker:  
  
-   O endereço do ponto de extremidade de serviço.  
  
-   A associação que o cliente deve usar para se conectar com esse ponto de extremidade. Nesse caso, wsHttpBinding definida pelo sistema é usado, apesar de ligações personalizadas podem ser definidas em arquivos de configuração do cliente. Para uso com o Windows Script Host, a associação personalizada é definida em um arquivo de Cscript.exe.config no mesmo diretório que Cscript.exe.  
  
-   O tipo do contrato que tem suporte no ponto de extremidade. Esse é o tipo que foi gerado e registrado acima. Como o script do Visual Basic fornece um ambiente de COM rigidez de tipos, um identificador para o contrato deve ser especificado. Esse GUID é o `interfaceID` de CalcProxy.tlb, que podem ser exibido usando COM ferramentas como o Visualizador de objeto OLE/COM (OleView.exe). Para ambientes fortemente tipadas, como Office VBA ou Visual Basic 6.0, adicionando uma referência explícita à biblioteca de tipos e, em seguida, declarar o tipo do objeto proxy podem ser usados no lugar do parâmetro de contrato. Isso também oferece suporte ao IntelliSense durante o desenvolvimento de aplicativos cliente.  
  
 Ter construído a instância do proxy com o moniker de serviço, o aplicativo cliente pode chamar métodos no proxy, o que resulta na infra-estrutura de moniker de serviço chamar as operações de serviço correspondentes.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Quando você executar o exemplo, a resposta da operação é exibida em uma janela de caixa de mensagem do Windows Script Host. Isso demonstra um cliente COM fazendo chamadas COM usando o moniker tipado para se comunicar com um serviço WCF. Apesar do uso de COM no aplicativo cliente, a comunicação com o serviço consiste apenas chamadas de serviço Web.  
  
## <a name="wsdl-contract"></a>Contrato WSDL  
 Para usar o moniker com um contrato WSDL, nenhum registro da biblioteca de cliente é necessário, mas o contrato WSDL para o serviço deve ser recuperado por meio de um mecanismo fora de banda, como usando um navegador para acessar o ponto de extremidade WSDL para o serviço. O identificador de origem, em seguida, pode acessar esse contrato em tempo de execução.  
  
 O aplicativo de cliente ComCalcClient.vbs usa o `FileSystemObject` para acessar o arquivo WSDL salvo localmente e, em seguida, novamente usa o `GetObject` função para construir um proxy para o serviço.  
  
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
  
 Especificam os parâmetros usados pelo moniker:  
  
-   O endereço do ponto de extremidade de serviço.  
  
-   A associação que o cliente deve usar para se conectar com esse ponto de extremidade e o namespace no qual essa associação é definida. Nesse caso, o `wsHttpBinding_ICalculator` é usado.  
  
-   O WSDL que define o contrato. Nesse caso, isso é a cadeia de caracteres que foi lido do arquivo serviceWsdl.xml.  
  
-   O nome e o namespace do contrato. Essa identificação é necessária porque a WSDL pode conter mais de um contrato.  
  
    > [!NOTE]
    >  Por padrão, o WCF services geram arquivos WSDL separados para cada namespace que o uso. Eles são vinculados com o uso da construção de importação WSDL. Porque o moniker espera que uma única definição de WSDL, o serviço deve usar um único namespace conforme demonstrado neste exemplo, ou os arquivos separados devem ser mesclados manualmente.  
  
 Ter construído a instância do proxy com o moniker de serviço, o aplicativo cliente pode chamar métodos no proxy, o que resulta na infra-estrutura de moniker de serviço chamar as operações de serviço correspondentes.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Quando você executar o exemplo, a resposta da operação é exibida em uma janela de caixa de mensagem do Windows Script Host. Isso demonstra um cliente COM fazendo chamadas COM usando o moniker com um contrato WSDL para se comunicar com um serviço WCF.  
  
## <a name="metadata-exchange-contract"></a>Contrato de troca de metadados  
 Para usar o moniker com um contrato MEX, assim como acontece com o contrato WSDL, nenhum registro de cliente é necessário. O contrato para o serviço é recuperado em tempo de execução através do uso interno de troca de metadados.  
  
 O aplicativo de cliente ComCalcClient.vbs novamente usa o `GetObject` função para construir um proxy para o serviço.  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 Especificam os parâmetros usados pelo moniker:  
  
-   O endereço do ponto de extremidade de troca de metadados de serviço.  
  
-   O endereço do ponto de extremidade de serviço.  
  
-   A associação que o cliente deve usar para se conectar com esse ponto de extremidade e o namespace no qual essa associação é definida. Nesse caso, o `wsHttpBinding_ICalculator` é usado.  
  
-   O nome e o namespace do contrato. Essa identificação é necessária porque a WSDL pode conter mais de um contrato.  
  
 Ter construído a instância do proxy com o moniker de serviço, o aplicativo cliente pode chamar métodos no proxy, o que resulta na infra-estrutura de moniker de serviço chamar as operações de serviço correspondentes.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Quando você executar o exemplo, a resposta da operação é exibida em uma janela de caixa de mensagem do Windows Script Host. Isso demonstra um cliente COM fazendo chamadas COM usando o moniker com um contrato MEX para se comunicar com um serviço WCF.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Para configurar e compilar o exemplo  
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. De um desenvolvedor de Prompt de comando para o Visual Studio, abra a pasta de \Client\Bin., sob a pasta de idioma específico.  
  
    > [!NOTE]
    >  Se você estiver usando [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 ou Windows Server 2008 R2, certifique-se de que você execute o prompt de comando com privilégios de administrador.  
  
4. Digite `tlbexp.exe client.dll /out:CalcProxy.tlb` para exportar a dll para um arquivo tlb. "Aviso de exportador da biblioteca de tipo" é esperado, mas não é um problema porque o tipo genérico não é necessário.  
  
5. Digite `regasm.exe /tlb:CalcProxy.tlb client.dll` para registrar os tipos com COM. "Aviso de exportador da biblioteca de tipo" é esperado, mas não é um problema porque o tipo genérico não é necessário.  
  
6. Digite `gacutil.exe /i client.dll` para adicionar o assembly no cache de Assembly Global.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador  
  
1. Teste que você pode acessar o serviço usando um navegador, digitando o seguinte endereço: `http://localhost/servicemodelsamples/service.svc`. Uma página de confirmação deve ser exibida na resposta.  
  
2. Execute ComCalcClient.vbs de \cliente, sob a pasta de idioma específico. Atividade do cliente é exibida nas janelas da caixa de mensagem.  
  
3. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1. No computador do serviço, crie um diretório virtual chamado ServiceModelSamples. O script de Setupvroot.bat incluído no exemplo pode ser usado para criar o diretório de disco e o diretório virtual.  
  
2. Copie os arquivos de programa do serviço de %SystemDrive%\Inetpub\wwwroot\servicemodelsamples ao diretório virtual ServiceModelSamples no computador do serviço. Certifique-se de incluir os arquivos no diretório \bin.  
  
3. Copie o arquivo de script de cliente na pasta \client, na pasta de idioma específico, para o computador cliente.  
  
4. No arquivo de script, altere o valor do endereço da definição do ponto de extremidade para coincidir com o novo endereço do seu serviço. Substitua todas as referências a "localhost" com um nome de domínio totalmente qualificado no endereço.  
  
5. Copie o arquivo WSDL para o computador cliente. No arquivo WSDL, serviceWsdl.xml, substitua todas as referências a "localhost" com um nome de domínio totalmente qualificado no endereço.  
  
6. Copie a biblioteca Client da pasta \Client\Bin., sob a pasta de idioma específico, para um diretório no computador cliente.  
  
7. Em um prompt de comando, navegue até esse diretório de destino no computador cliente. Se usando [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], certifique-se de executar o prompt de comando como administrador.  
  
8. Digite `tlbexp.exe client.dll /out:CalcProxy.tlb` para exportar a dll para um arquivo tlb. "Aviso de exportador da biblioteca de tipo" é esperado, mas não é um problema porque o tipo genérico não é necessário.  
  
9. Digite `regasm.exe /tlb:CalcProxy.tlb client.dll` para registrar os tipos com COM. Verifique se esse caminho foi definido para a pasta que contém `regasm.exe` antes de executar o comando.  
  
10. Digite `gacutil.exe /i client.dll` para adicionar o assembly no cache de Assembly Global. Verifique se esse caminho foi definido para a pasta que contém `gacutil.exe` antes de executar o comando.  
  
11. Teste que você pode acessar o serviço do computador cliente usando um navegador.  
  
12. No computador cliente, inicie ComCalcClient.vbs.  
  
#### <a name="to-clean-up-after-the-sample"></a>Para limpar após a amostra  
  
-   Para fins de segurança, remova a definição do diretório virtual e as permissões concedidas nas etapas de configuração quando tiver terminado com os exemplos.  
