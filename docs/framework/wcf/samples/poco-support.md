---
title: Suporte para POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: e94f6d9576ed96613d975a66c1965820002f94ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183411"
---
# <a name="poco-support"></a>Suporte para POCO
Esta amostra demonstra o suporte à serialização para tipos não marcados; ou seja, tipos aos quais os atributos de serialização não foram aplicados, às vezes referidos como tipos de Simples Objeto CLR Antigo (POCO). O <xref:System.Runtime.Serialization.DataContractSerializer> infere um contrato de dados para todos os tipos públicos não marcados que tenham um construtor sem parâmetros. Os contratos de dados permitem que você passe dados estruturados de e para serviços. Para obter mais informações sobre tipos não marcados, consulte [Tipos Serializable](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Esta amostra é baseada no [Getting Started,](../../../../docs/framework/wcf/samples/getting-started-sample.md)mas usa números complexos em vez de tipos numéricos primitivos. Também é semelhante à amostra do Contrato <xref:System.Runtime.Serialization.DataContractAttribute> de <xref:System.Runtime.Serialization.DataMemberAttribute> [Dados Básicos,](../../../../docs/framework/wcf/samples/basic-data-contract.md) exceto que os e atributos não são utilizados.  
  
 O serviço é hospedado pelo Internet Information Services (IIS) e o cliente é um aplicativo de console (.exe).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 A `ComplexNumber` classe é `ServiceContract`usada no . O `ComplexNumber` tipo não <xref:System.Runtime.Serialization.DataContractAttribute> tem <xref:System.Runtime.Serialization.DataMemberAttribute> os atributos e atributos, como mostrado no código de amostra a seguir. Por padrão, todas as propriedades e campos públicos são serializados.  
  
```csharp
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
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Confira também

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [Tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md)
