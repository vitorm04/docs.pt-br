---
title: Exemplo de serviço de AJAX utilizando tipos complexos
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 4574e5d33ebed7184e229c71e03496db34a95575
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528279"
---
# <a name="ajax-service-using-complex-types-sample"></a>Exemplo de serviço de AJAX utilizando tipos complexos
Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço ASP.NET Asynchronous JavaScript and XML (AJAX) que cria instâncias de tipos complexos e envia-os entre o cliente como notação JSON (JavaScript Object) e o serviço. Você pode acessar um serviço AJAX usando código JavaScript de um cliente de navegador da Web. Este exemplo se baseia a [serviço de AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo.  
  
 Suporte a AJAX no WCF é otimizado para uso com o ASP.NET AJAX por meio de <xref:System.Web.UI.ScriptManager> controle. Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte o [amostras do AJAX](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O serviço no exemplo a seguir é um serviço WCF, sem nenhum código específico do AJAX. Porque o <xref:System.ServiceModel.Web.WebGetAttribute> atributo não for aplicado, o verbo HTTP padrão ("POST") é usado. O serviço tem uma operação, `DoMath`, que retorna um tipo complexo chamado `MathResult`. O tipo complexo é um tipo de contrato de dados padrão, que também não contém nenhum código específico do AJAX.  

```csharp
[DataContract]  
public class MathResult  
{  
    [DataMember]  
    public double sum;  
    [DataMember]  
    public double difference;  
    [DataMember]  
    public double product;  
    [DataMember]  
    public double quotient;  
}  
```

 Criar um ponto de extremidade do AJAX no serviço usando o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, assim como no exemplo de serviço básico do AJAX.  
  
 O cliente ComplexTypeClientPage.aspx de página da Web contém código ASP.NET e JavaScript para invocar o serviço quando o usuário clica o **executar o cálculo** botão na página. O código para invocar o serviço constrói um corpo JSON e envia-o usando HTTP POST, semelhante do [serviço de AJAX usando o HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) exemplo.  
  
 Depois que a chamada de serviço for bem-sucedida, você pode acessar os membros de dados individuais (`sum`, `difference`, `product` e `quotient`) sobre o JavaScript resultante do objeto.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Compile a solução ComplexTypeAjaxService.sln, conforme descrito em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Navegue até http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (não abrir ComplexTypeClientPage.aspx no navegador do diretório do projeto).  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a>Consulte também  
 [Serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
