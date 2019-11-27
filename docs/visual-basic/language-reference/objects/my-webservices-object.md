---
title: Objeto My.WebServices
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 290d025985663bc45fe605a2e9904fc90fb2bc63
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350345"
---
# <a name="mywebservices-object"></a>Objeto My.WebServices
Fornece propriedades para criar e acessar uma única instância de cada serviço Web XML referenciado pelo projeto atual.  
  
## <a name="remarks"></a>Comentários  
 O objeto `My.WebServices` fornece uma instância de cada serviço Web referenciado pelo projeto atual. Cada instância é instanciada sob demanda. É possível acessar esses serviços Web por meio das propriedades do objeto `My.WebServices`. O nome da propriedade é igual ao nome do serviço Web acessado pela propriedade. Qualquer classe que herda de <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> é um serviço Web. Para obter informações sobre como adicionar serviços Web a um projeto, consulte [acessando serviços Web de aplicativos](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 O objeto `My.WebServices` expõe apenas os serviços Web associados ao projeto atual. Ele não fornece acesso a serviços Web declarados em DLLs referenciadas. Para acessar um serviço Web que uma DLL fornece, você deve usar o nome qualificado do serviço Web, no formato *DllName*. *WebServiceName*. Para obter mais informações, consulte [acessando serviços Web de aplicativos](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 O objeto e suas propriedades não estão disponíveis para aplicativos Web.  
  
## <a name="properties"></a>{1&gt;Propriedades&lt;1}  
 Cada propriedade do objeto `My.WebServices` fornece acesso a uma instância de um serviço Web referenciado pelo projeto atual. O nome da propriedade é o mesmo que o nome do serviço Web que a propriedade acessa, e o tipo de propriedade é o mesmo que o tipo do serviço Web.  
  
> [!NOTE]
> Se houver uma colisão de nomes, o nome da propriedade para acessar um serviço Web será *RootNamespace*_*namespace*\_*ServiceName*. Por exemplo, considere dois serviços Web chamados `Service1`. Se um desses serviços estiver no namespace raiz `WindowsApplication1` e no namespace `Namespace1`, você acessaria esse serviço usando `My.WebServices.WindowsApplication1_Namespace1_Service1`.  
  
 Quando você acessa pela primeira vez uma das propriedades do objeto `My.WebServices`, ele cria uma nova instância do serviço Web e a armazena. Os acessos subsequentes dessa propriedade retornam essa instância do serviço Web.  
  
 Você pode descartar um serviço Web atribuindo `Nothing` à propriedade para esse serviço Web. O setter da propriedade atribui `Nothing` ao valor armazenado. Se você atribuir qualquer valor diferente de `Nothing` à propriedade, o setter lançará uma exceção de <xref:System.ArgumentException>.  
  
 Você pode testar se uma propriedade do objeto de `My.WebServices` armazena uma instância do serviço Web usando o operador `Is` ou `IsNot`. Você pode usar esses operadores para verificar se o valor da propriedade é `Nothing`.  
  
> [!NOTE]
> Normalmente, o operador `Is` ou `IsNot` precisa ler o valor da propriedade para executar a comparação. No entanto, se a propriedade atualmente armazena `Nothing`, a propriedade cria uma nova instância do serviço Web e, em seguida, retorna essa instância. No entanto, o compilador de Visual Basic trata as propriedades do objeto `My.WebServices` especialmente e permite que o operador `Is` ou `IsNot` Verifique o status da propriedade sem alterar seu valor.  
  
## <a name="example"></a>Exemplo  
 Este exemplo chama o método `FahrenheitToCelsius` do `TemperatureConverter` Web Service XML e retorna o resultado.  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 Para que este exemplo funcione, seu projeto deve fazer referência a um serviço Web chamado `Converter`e esse serviço Web deve expor o método `ConvertTemperature`. Para obter mais informações, consulte [acessando serviços Web de aplicativos](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Esse código não funciona em um projeto de aplicativo Web.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
  
### <a name="availability-by-project-type"></a>Disponibilidade por tipo de projeto  
  
|Tipo de projeto|Disponível|  
|---|---|  
|Aplicativo do Windows|**Sim**|  
|Biblioteca de classes|**Sim**|  
|Aplicativo do Console|**Sim**|  
|Biblioteca de controle do Windows|**Sim**|  
|Biblioteca de controle da Web|**Sim**|  
|Serviço do Windows|**Sim**|  
|Site da Web|Não|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [Acessando serviços Web do aplicativo](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
