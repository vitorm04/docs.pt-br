---
title: "Codificação de MTOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 46984ea1ac08aa1128a4f32144285f590eafb6c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="mtom-encoding"></a>Codificação de MTOM
Este exemplo demonstra o uso da mensagem de mecanismo de otimização de transmissão da mensagem (MTOM) a codificação com WSHttpBinding. MTOM é um mecanismo para transmissão de grandes anexos binários com mensagens SOAP como bytes brutos, permitindo a mensagens menores.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Por padrão, o WSHttpBinding envia e as mensagens recebidas como texto normal XML. Para habilitar o envio e recebimento de mensagens MTOM, defina o `messageEncoding` atributo na configuração da associação (como o código de exemplo a seguir), ou diretamente em associação com o `MessageEncoding` propriedade. O serviço ou cliente agora pode enviar e receber mensagens MTOM.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 O codificador MTOM pode otimizar a matrizes de bytes e fluxos. Neste exemplo, a operação usa um `Stream` parâmetro e, portanto, podem ser otimizados.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```  
  
 O contrato escolhido para este exemplo transmite dados binários para o serviço e recebe o número de bytes carregados como o valor de retorno. Quando o serviço está instalado e o cliente é executado, exibe o número 1000, o que indica que todos os 1.000 bytes foram recebidos. O restante da saída lista os tamanhos de mensagem otimizados e não otimizados para várias cargas.  
  
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
  
 A finalidade de uso MTOM é otimizar a transmissão de grandes cargas binárias. Enviando uma mensagem SOAP usando MTOM tem uma sobrecarga notável para pequenas cargas binárias, mas se torna uma grande economia quando elas crescem em alguns milhares de bytes. A razão para isso é normal texto XML codifica dados binários usando Base64, que requer quatro caracteres para todos os três bytes e aumenta o tamanho dos dados em um terceiro. MTOM é capaz de transmitir dados binários como bytes brutos, economizando tempo de codificação/decodificação e resultante é mensagens menores. O limite de alguns milhares de bytes é pequeno em comparação com os documentos de negócios atuais e fotos digitais.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também
