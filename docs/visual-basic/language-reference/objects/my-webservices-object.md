---
title: Meu objeto. WebServices (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: c887f9b7c5a41c0aa02016354c46d5507b103d25
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918175"
---
# <a name="mywebservices-object"></a>Objeto My.WebServices
Fornece propriedades para criar e acessar uma única instância de cada serviço Web XML referenciado pelo projeto atual.  
  
## <a name="remarks"></a>Comentários  
 O objeto `My.WebServices` fornece uma instância de cada serviço Web referenciado pelo projeto atual. Cada instância é instanciada sob demanda. É possível acessar esses serviços Web por meio das propriedades do objeto `My.WebServices`. O nome da propriedade é igual ao nome do serviço Web acessado pela propriedade. Qualquer classe que herda de <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> é um serviço Web. Para obter informações sobre como adicionar serviços Web a um projeto, consulte Acessando [Serviços Web de aplicativos](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 O `My.WebServices` objeto expõe apenas os serviços Web associados ao projeto atual. Ele não fornece acesso a serviços Web declarados em DLLs referenciadas. Para acessar um serviço Web que uma DLL fornece, você deve usar o nome qualificado do serviço Web, no formato *DllName*.WebServiceName. Para obter mais informações, consulte Acessando [Serviços Web de aplicativos](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 O objeto e suas propriedades não estão disponíveis para aplicativos Web.  
  
## <a name="properties"></a>Propriedades  
 Cada propriedade do `My.WebServices` objeto fornece acesso a uma instância de um serviço Web referenciado pelo projeto atual. O nome da propriedade é o mesmo que o nome do serviço Web que a propriedade acessa, e o tipo de propriedade é o mesmo que o tipo do serviço Web.  
  
> [!NOTE]
> Se houver uma colisão de nomes, o nome da propriedade para acessar um serviço Web será *RootNamespace*_*namespace*\_ServiceName. Por exemplo, considere dois serviços Web denominados `Service1`. Se um desses serviços estiver no namespace `WindowsApplication1` raiz e no namespace `Namespace1`, você acessaria esse serviço usando `My.WebServices.WindowsApplication1_Namespace1_Service1`o.  
  
 Quando você acessa pela primeira vez uma `My.WebServices` das propriedades do objeto, ele cria uma nova instância do serviço Web e a armazena. Os acessos subsequentes dessa propriedade retornam essa instância do serviço Web.  
  
 Você pode descartar um serviço Web atribuindo `Nothing` à propriedade para esse serviço Web. O setter da propriedade é atribuído `Nothing` ao valor armazenado. Se você atribuir qualquer valor diferente `Nothing` de à propriedade, o setter lançará uma <xref:System.ArgumentException> exceção.  
  
 Você pode testar se uma propriedade do `My.WebServices` objeto armazena uma instância do serviço Web usando o `Is` operador or `IsNot` . Você pode usar esses operadores para verificar se o valor da propriedade é `Nothing`.  
  
> [!NOTE]
> Normalmente, o `Is` operador `IsNot` or precisa ler o valor da propriedade para executar a comparação. No entanto, se a propriedade `Nothing`atualmente armazena, a propriedade cria uma nova instância do serviço Web e, em seguida, retorna essa instância. No entanto, o compilador de Visual Basic trata as `My.WebServices` Propriedades do objeto especialmente e permite `Is` que `IsNot` o operador OR Verifique o status da propriedade sem alterar seu valor.  
  
## <a name="example"></a>Exemplo  
 Este exemplo chama o `FahrenheitToCelsius` método `TemperatureConverter` do serviço Web XML e retorna o resultado.  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 Para que este exemplo funcione, seu projeto deve fazer referência a um serviço `Converter`Web chamado e esse serviço Web deve expor `ConvertTemperature` o método. Para obter mais informações, consulte Acessando [Serviços Web de aplicativos](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
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

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [Acessando serviços Web do aplicativo](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
