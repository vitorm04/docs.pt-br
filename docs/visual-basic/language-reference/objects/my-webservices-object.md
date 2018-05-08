---
title: Objeto My.WebServices
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 9519638c7609b9b1d0f5e07397c46975e2696c94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="mywebservices-object"></a>Objeto My.WebServices
Fornece propriedades para criar e acessar uma única instância de cada serviço Web XML referenciado pelo projeto atual.  
  
## <a name="remarks"></a>Comentários  
 O objeto `My.WebServices` fornece uma instância de cada serviço Web referenciado pelo projeto atual. Cada instância é instanciada sob demanda. É possível acessar esses serviços Web por meio das propriedades do objeto `My.WebServices`. O nome da propriedade é igual ao nome do serviço Web acessado pela propriedade. Qualquer classe que herda de <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> é um serviço Web. Para obter informações sobre como adicionar os serviços da Web a um projeto, consulte [acessar o aplicativo Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 O `My.WebServices` objeto expõe apenas os serviços Web associados ao projeto atual. Ele não fornece acesso a serviços Web declarado em DLLs referenciados. Para acessar um serviço Web que fornece uma DLL, você deve usar o nome qualificado do serviço da Web, no formato *Nomedadll*. *WebServiceName*. Para obter mais informações, consulte [acessar o aplicativo Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 O objeto e suas propriedades não estão disponíveis para aplicativos da Web.  
  
## <a name="properties"></a>Propriedades  
 Cada propriedade do `My.WebServices` objeto fornece acesso a uma instância de um serviço Web referenciado pelo projeto atual. O nome da propriedade é igual ao nome do serviço Web que acessa a propriedade e o tipo de propriedade é o mesmo tipo do serviço Web.  
  
> [!NOTE]
>  Se houver uma colisão de nomes, o nome da propriedade para acessar um serviço Web é *RootNamespace*_*Namespace*\_*ServiceName*. Por exemplo, considere dois serviços da Web denominados `Service1`. Se um desses serviços é o namespace raiz `WindowsApplication1` e no namespace `Namespace1`, você acessaria o serviço usando `My.WebServices.WindowsApplication1_Namespace1_Service1`.  
  
 Quando você acessa pela primeira vez um do `My.WebServices` propriedades do objeto, ele cria uma nova instância do serviço Web e os armazena. Acessa subsequente dessa propriedade retorna essa instância do serviço Web.  
  
 Você pode descartar um serviço Web atribuindo `Nothing` para a propriedade para o serviço Web. O setter da propriedade atribui `Nothing` ao valor armazenado. Se você atribuir qualquer valor diferente de `Nothing` para a propriedade setter lança um <xref:System.ArgumentException> exceção.  
  
 Você pode testar se uma propriedade do `My.WebServices` objeto armazena uma instância do serviço da Web usando o `Is` ou `IsNot` operador. Você pode usar os operadores para verificar se o valor da propriedade é `Nothing`.  
  
> [!NOTE]
>  Normalmente, o `Is` ou `IsNot` operador precisa ler o valor da propriedade para executar a comparação. No entanto, se a propriedade armazena atualmente `Nothing`, a propriedade cria uma nova instância do serviço Web e, em seguida, retorna essa instância. No entanto, o compilador do Visual Basic trata as propriedades do `My.WebServices` especialmente do objeto e permite que o `Is` ou `IsNot` operador para verificar o status da propriedade sem alterar seu valor.  
  
## <a name="example"></a>Exemplo  
 Este exemplo chama o `FahrenheitToCelsius` método o `TemperatureConverter` XML Web Services e retorna o resultado.  
  
 [!code-vb[VbVbalrMyWebService#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-webservices-object_1.vb)]  
  
 Para esse exemplo funcione, seu projeto deve fazer referência a um serviço Web chamado `Converter`, e o serviço da Web deve expor o `ConvertTemperature` método. Para obter mais informações, consulte [acessar o aplicativo Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Esse código não funciona em um projeto de aplicativo Web.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="availability-by-project-type"></a>Disponibilidade por tipo de projeto  
  
|Tipo de projeto|Disponível|  
|---|---|  
|Aplicativo do Windows|**Sim**|  
|Biblioteca de Classes|**Sim**|  
|Aplicativo do Console|**Sim**|  
|Biblioteca de controle do Windows|**Sim**|  
|Biblioteca de controle da Web|**Sim**|  
|Serviço do Windows|**Sim**|  
|Site da Web|Não|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>  
 <xref:System.ArgumentException>  
 [Acessando serviços Web do aplicativo](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
