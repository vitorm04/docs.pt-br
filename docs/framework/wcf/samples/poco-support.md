---
title: Suporte para POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: ab95469afa53bd0b27efc451875d4912db74a45a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501980"
---
# <a name="poco-support"></a>Suporte para POCO
Este exemplo demonstra o suporte de serialização para tipos desmarcados. ou seja, tipos aos quais atributos de serialização não foram aplicados, às vezes chamado de tipos simples antigo CLR Object (POCO). O <xref:System.Runtime.Serialization.DataContractSerializer> infere um contrato de dados para todos os tipos de desmarcados públicos que tem um construtor padrão. Contratos de dados permitem que você transmita dados estruturados para e de serviços. Para obter mais informações sobre tipos desmarcados, consulte [tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), mas usa números complexos em vez de tipos numéricos primitivo. Também é semelhante ao [contrato de dados básico](../../../../docs/framework/wcf/samples/basic-data-contract.md) de exemplo, exceto que o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos não são usados.  
  
 O serviço é hospedado por serviços de informações da Internet (IIS) e o cliente é um aplicativo de console (.exe).  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O `ComplexNumber` classe é usada no `ServiceContract`. O `ComplexNumber` tipo não tem o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos, como mostrado no código de exemplo a seguir. Por padrão, todas as propriedades públicas e campos são serializados.  
  
```  
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 [Tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md)
