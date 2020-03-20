---
title: Codificação de MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 83dbe9e51da1cc9e55bfffb862e2601d70fc7695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144377"
---
# <a name="mtom-encoding"></a>Codificação de MTOM
Esta amostra demonstra o uso da codificação de mensagem MTOM (Message Transmission Optimization Mechanism, mecanismo de otimização de transmissão de mensagens) com um WSHttpBinding. MTOM é um mecanismo para transmitir grandes anexos binários com mensagens SOAP como bytes brutos, permitindo mensagens menores.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Por padrão, o WSHttpBinding envia e recebe mensagens como xML de texto normal. Para habilitar o envio e o `messageEncoding` recebimento de mensagens MTOM, defina o atributo na `MessageEncoding` configuração da vinculação (como no código de exemplo a seguir) ou diretamente na vinculação usando a propriedade. O serviço ou cliente agora pode enviar e receber mensagens MTOM.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 O codificador MTOM pode otimizar matrizes de bytes e fluxos. Nesta amostra, a operação `Stream` utiliza um parâmetro e, portanto, pode ser otimizada.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 O contrato escolhido para esta amostra transmite dados binários para o serviço e recebe o número de bytes carregados como o valor de retorno. Quando o serviço é instalado e o cliente é executado, ele imprime o número 1000, o que indica que todos os 1000 bytes foram recebidos. O restante da saída lista tamanhos de mensagens otimizados e não otimizados para várias cargas.  
  
```console
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 O objetivo de usar o MTOM é otimizar a transmissão de grandes cargas binárias. O envio de uma mensagem SOAP usando MTOM tem uma sobrecarga perceptível para pequenas cargas binárias, mas torna-se uma grande economia quando eles crescem mais de alguns milhares de bytes. A razão para isso é que o XML de texto normal codifica dados binários usando base64, que requer quatro caracteres para cada três bytes, e aumenta o tamanho dos dados em um terço. O MTOM é capaz de transmitir dados binários como bytes brutos, salvando o tempo de codificação/decodificação e resultando em mensagens menores. O limiar de alguns milhares de bytes é pequeno quando comparado com os documentos de negócios e fotografias digitais de hoje.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Instale ASP.NET 4.0 usando o seguinte comando.  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
