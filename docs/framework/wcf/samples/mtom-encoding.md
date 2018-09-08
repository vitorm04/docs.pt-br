---
title: Codificação de MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: f54a22b0004623c8aef8f2788ed7d59f7d777ce7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44128244"
---
# <a name="mtom-encoding"></a>Codificação de MTOM
Este exemplo demonstra o uso da mensagem MTOM Message Transmission Optimization Mechanism () codificação com WSHttpBinding. MTOM é um mecanismo para a transmissão de anexos binários grandes com mensagens SOAP como bytes brutos, permitindo mensagens menores.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Por padrão, o WSHttpBinding envia e as mensagens recebidas como XML de texto normal. Para habilitar o envio e recebimento de mensagens MTOM, defina as `messageEncoding` atributo na configuração da associação (como no seguinte exemplo de código), ou diretamente na associação usando o `MessageEncoding` propriedade. O serviço ou cliente agora pode enviar e receber mensagens MTOM.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 O codificador MTOM pode otimizar as matrizes de bytes e fluxos. Neste exemplo, a operação usa um `Stream` parâmetro e, portanto, pode ser otimizada.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 O contrato escolhido para este exemplo transmite dados binários para o serviço e recebe o número de bytes carregados como o valor de retorno. Quando o serviço está instalado e o cliente é executado, ele imprime o número 1000, o que indica que todos os 1.000 bytes foram recebidos. O restante da saída lista os tamanhos de mensagem otimizados e não otimizados para várias cargas.  
  
```  
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
  
 A finalidade para usar o MTOM é otimizar a transmissão de grandes cargas de binárias. Enviando uma mensagem SOAP usando MTOM tem uma sobrecarga considerável para transferências binárias pequenas, mas se torna uma grande economia quando elas aumentarem ao longo de alguns milhares de bytes. A razão para isso é que o texto normal XML codifica dados binários usando Base64, que requer quatro caracteres para todos os três bytes e aumenta o tamanho dos dados em um terço. MTOM é capaz de transmitir dados binários como bytes brutos, economizando o tempo de codificação/decodificação e resultante é mensagens menores. O limite de alguns milhares de bytes é pequeno em comparação com os documentos de negócios de hoje e fotografias digitais.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também
