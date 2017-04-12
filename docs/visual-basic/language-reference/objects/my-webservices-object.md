---
title: Objeto My. WebServices | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
dev_langs:
- VB
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9c05238738f4748831c7e55ea4279bb83ae9f835
ms.lasthandoff: 03/13/2017

---
# <a name="mywebservices-object"></a>Objeto My.WebServices
Fornece propriedades para criar e acessar uma única instância de cada serviço Web XML referenciado pelo projeto atual.  
  
## <a name="remarks"></a>Comentários  
 O `My.WebServices` objeto fornece uma instância de cada serviço Web referenciado pelo projeto atual. Cada instância é instanciada por demanda. Você pode acessar esses serviços da Web através das propriedades do `My.WebServices` objeto. O nome da propriedade é igual ao nome do serviço Web que acessa a propriedade. Qualquer classe que herda de <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>é um serviço Web.</xref:System.Web.Services.Protocols.SoapHttpClientProtocol> Para obter informações sobre como adicionar os serviços da Web a um projeto, consulte [acessar o aplicativo Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 O `My.WebServices` objeto expõe apenas os serviços Web associados ao projeto atual. Ele não fornece acesso aos Web services declarados em DLLs referenciados. Para acessar um serviço Web que fornece uma DLL, você deve usar o nome qualificado do serviço da Web, no formulário *DllName*.* WebServiceName*. Para obter mais informações, consulte [acessar o aplicativo Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 O objeto e suas propriedades não estão disponíveis para aplicativos da Web.  
  
## <a name="properties"></a>Propriedades  
 Cada propriedade do `My.WebServices` objeto fornece acesso a uma instância de um serviço Web referenciado pelo projeto atual. O nome da propriedade é igual ao nome do serviço Web que acessa a propriedade e o tipo de propriedade é o mesmo tipo do serviço Web.  
  
> [!NOTE]
>  Se houver uma colisão de nomes, o nome da propriedade para acessar um serviço da Web é *RootNamespace*_*Namespace*\_*ServiceName*. Por exemplo, considere dois serviços Web chamados `Service1`. Se um desses serviços é o namespace raiz `WindowsApplication1` e no namespace `Namespace1`, você poderia acessar esse serviço usando `My.WebServices.WindowsApplication1_Namespace1_Service1`.  
  
 Quando você acessa pela primeira vez um do `My.WebServices` propriedades do objeto, ele cria uma nova instância do serviço da Web e o armazena. Os acessos subsequentes dessa propriedade retornam essa instância do serviço da Web.  
  
 Você pode descartar um serviço da Web atribuindo `Nothing` para a propriedade para o serviço da Web. Atribui o setter da propriedade `Nothing` para o valor armazenado. Se você atribuir qualquer valor diferente de `Nothing` à propriedade setter lança um <xref:System.ArgumentException>exceção.</xref:System.ArgumentException>  
  
 Você pode testar se uma propriedade do `My.WebServices` objeto armazena uma instância do serviço da Web usando o `Is` ou `IsNot` operador. Você pode usar os operadores para verificar se o valor da propriedade é `Nothing`.  
  
> [!NOTE]
>  Normalmente, o `Is` ou `IsNot` operador precisa ler o valor da propriedade para executar a comparação. No entanto, se a propriedade armazena atualmente `Nothing`, a propriedade cria uma nova instância do serviço da Web e, em seguida, retorna essa instância. No entanto, o compilador Visual Basic trata as propriedades do `My.WebServices` especialmente de objeto e permite que o `Is` ou `IsNot` operador para verificar o status da propriedade sem alterar seu valor.  
  
## <a name="example"></a>Exemplo  
 Este exemplo chama o `FahrenheitToCelsius` método o `TemperatureConverter` XML Web Services e retorna o resultado.  
  
 [!code-vb[VbVbalrMyWebService n º&1;](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-webservices-object_1.vb)]  
  
 Para esse exemplo funcione, seu projeto deve fazer referência a um serviço Web denominado `Converter`, e o serviço Web deve expor o `ConvertTemperature` método. Para obter mais informações, consulte [acessar o aplicativo Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Esse código não funciona em um projeto de aplicativo Web.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="availability-by-project-type"></a>Disponibilidade por tipo de projeto  
  
|Tipo de projeto|Disponível|  
|---|---|  
|Aplicativo do Windows|**Sim**|  
|Biblioteca de Classes|**Sim**|  
|Aplicativo do Console|**Sim**|  
|Biblioteca de controle do Windows|**Sim**|  
|Biblioteca de Controles da Web|**Sim**|  
|Serviço do Windows|**Sim**|  
|Site|Não|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol></xref:System.Web.Services.Protocols.SoapHttpClientProtocol>   
 <xref:System.ArgumentException></xref:System.ArgumentException>   
 [Acessando serviços Web do aplicativo](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
