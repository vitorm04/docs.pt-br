---
title: Objeto My. WebServices (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 7ae99bec5797591e53c6c77f5d9f88589352104c
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "40240340"
---
# <a name="mywebservices-object"></a>Objeto My.WebServices
Fornece propriedades para criar e acessar uma única instância de cada serviço Web XML referenciado pelo projeto atual.  
  
## <a name="remarks"></a>Comentários  
 O objeto `My.WebServices` fornece uma instância de cada serviço Web referenciado pelo projeto atual. Cada instância é instanciada sob demanda. É possível acessar esses serviços Web por meio das propriedades do objeto `My.WebServices`. O nome da propriedade é igual ao nome do serviço Web acessado pela propriedade. Qualquer classe que herda de <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> é um serviço Web. Para obter informações sobre como adicionar os serviços da Web a um projeto, consulte [acessar o aplicativo Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 O `My.WebServices` objeto expõe apenas os serviços Web associados ao projeto atual. Ele não fornece acesso aos serviços da Web declarados em DLLs referenciadas. Para acessar um serviço Web que fornece uma DLL, você deve usar o nome qualificado do serviço Web, na forma *DllName*. *WebServiceName*. Para obter mais informações, consulte [acessar o aplicativo Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 O objeto e suas propriedades não estão disponíveis para aplicativos da Web.  
  
## <a name="properties"></a>Propriedades  
 Cada propriedade do `My.WebServices` objeto fornece acesso a uma instância de um serviço Web referenciado pelo projeto atual. O nome da propriedade é igual ao nome do serviço Web que acessa a propriedade e o tipo de propriedade é o mesmo tipo do serviço Web.  
  
> [!NOTE]
>  Se houver uma colisão de nomes, o nome da propriedade para acessar um serviço Web está *RootNamespace*_*Namespace*\_*ServiceName*. Por exemplo, considere dois serviços Web denominados `Service1`. Se um desses serviços é no namespace raiz `WindowsApplication1` e no namespace `Namespace1`, você acessaria esse serviço usando `My.WebServices.WindowsApplication1_Namespace1_Service1`.  
  
 Quando você acessa pela primeira vez um do `My.WebServices` propriedades do objeto, ele cria uma nova instância do serviço Web e os armazena. Acessos subsequentes dessa propriedade retornam essa instância do serviço Web.  
  
 Você pode descartar um serviço Web por meio da atribuição `Nothing` à propriedade para o serviço Web. Atribui o setter da propriedade `Nothing` ao valor armazenado. Se você atribuir qualquer valor diferente de `Nothing` à propriedade setter lança um <xref:System.ArgumentException> exceção.  
  
 Você pode testar se uma propriedade do `My.WebServices` objeto armazena uma instância do serviço Web usando o `Is` ou `IsNot` operador. Você pode usar esses operadores para verificar se o valor da propriedade é `Nothing`.  
  
> [!NOTE]
>  Normalmente, o `Is` ou `IsNot` operador tem de ler o valor da propriedade para executar a comparação. No entanto, se a propriedade atualmente armazena `Nothing`, a propriedade cria uma nova instância do serviço Web e, em seguida, retorna essa instância. No entanto, o compilador do Visual Basic trata as propriedades do `My.WebServices` especialmente de objeto e permite que o `Is` ou `IsNot` operador para verificar o status da propriedade sem alterar seu valor.  
  
## <a name="example"></a>Exemplo  
 Este exemplo chama o `FahrenheitToCelsius` método da `TemperatureConverter` serviço Web XML e retorna o resultado.  
  
 [!code-vb[VbVbalrMyWebService#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-webservices-object_1.vb)]  
  
 Para esse exemplo funcione, seu projeto deve fazer referência a um serviço Web denominado `Converter`, e esse serviço Web deve expor a `ConvertTemperature` método. Para obter mais informações, consulte [acessar o aplicativo Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
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
