---
title: "Objeto My.WebServices | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "My.WebServices"
  - "My.MyProject.WebServices"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Objeto My.WebServices"
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Objeto My.WebServices
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Fornece propriedades para criar e acessar uma única instância de cada serviço XML da Web referenciado pelo projeto atual.  
  
## Comentários  
 O objeto `My.WebServices` fornece uma instância de cada Serviço Web referenciado pelo projeto atual.  Cada instância é instanciada por demanda.  Você pode acessar esses serviços da Web através das propriedades do objeto `My.WebServices`.  O nome da propriedade é o mesmo que o nome do serviço Web que a propriedade acessa.  Qualquer classe que herda de <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> é um serviço Web.  Para obter informações sobre como adicionar os serviços da Web a um projeto, consulte [Acessando serviços Web do aplicativo](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 O `My.WebServices` objeto expõe apenas os serviços da Web associados ao projeto atual.  Ele não fornece acesso aos serviços da Web declarado em DLLs referenciadas.  Para acessar um serviço da Web que fornece a uma DLL, você deve usar o nome qualificado do serviço da Web, no formulário  *DllName*. *WebServiceName*.  Para obter mais informações, consulte [Acessando serviços Web do aplicativo](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 O objeto e suas propriedades não estão disponíveis para aplicativos da Web.  
  
## Propriedades  
 Cada propriedade da `My.WebServices` objeto fornece acesso a uma instância de um serviço Web referenciado pelo projeto atual.  O nome da propriedade é o mesmo que o nome do serviço da Web que a acessa a propriedade e o tipo de propriedade é o mesmo que o tipo do serviço Web.  
  
> [!NOTE]
>  Se houver um conflito de nome, o nome de propriedade para acessar um serviço da Web é  *RootNamespace*\_*espaço para nome*\_*ServiceName*.  Por exemplo, considere dois serviços da Web chamados `Service1`.  Se um desses serviços está no namespace raiz `WindowsApplication1` e no namespace `Namespace1`, você poderia acessar esse serviço usando `My.WebServices.WindowsApplication1_Namespace1_Service1`.  
  
 Quando você acessa pela primeira vez um do `My.WebServices` propriedades do objeto, ele cria uma nova instância do serviço da Web e o armazena.  Os acessos subseqüentes dessa propriedade retornam essa instância do serviço da Web.  
  
 Você pode descartar um serviço da Web atribuindo `Nothing` para a propriedade para o serviço da Web.  A propriedade setter atribui `Nothing` para o valor armazenado.  Se você atribuir qualquer valor diferente de `Nothing` à propriedade, o setter lança um <xref:System.ArgumentException> exceção.  
  
 Você pode testar se uma propriedade da `My.WebServices` objeto armazena uma instância do serviço da Web usando o `Is` ou `IsNot` operador.  Você pode usar esses operadores para verificar se o valor da propriedade é `Nothing`.  
  
> [!NOTE]
>  Normalmente, o `Is` ou `IsNot` operador tem que ler o valor da propriedade para executar a comparação.  No entanto, se a propriedade atualmente armazena `Nothing`, a propriedade cria uma nova instância do serviço da Web e, em seguida, retorna essa instância.  No entanto, o compilador Visual Basic trata as propriedades da `My.WebServices` especialmente de objeto e permite que o `Is` ou `IsNot` operador para verificar o status da propriedade sem alterar seu valor.  
  
## Exemplo  
 Este exemplo chama o `FahrenheitToCelsius` método da `TemperatureConverter` XML Web Services e retorna o resultado.  
  
 [!code-vb[VbVbalrMyWebService#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-webservices-object_1.vb)]  
  
 Para esse exemplo funcione, seu projeto deve fazer referência a um serviço da Web chamado `Converter`, e o serviço da Web deve expor a `ConvertTemperature` método.  Para obter mais informações, consulte [Acessando serviços Web do aplicativo](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Esse código não funciona em um projeto de aplicativo da Web.  
  
## Requisitos  
  
### Disponibilidade por Tipo de Projeto  
  
|||  
|-|-|  
|Tipo de Projeto|Disponível|  
|Aplicativo do Windows|**Sim**|  
|Biblioteca de Classe|**Sim**|  
|Aplicativo de Console|**Sim**|  
|Biblioteca de Controle do Windows|**Sim**|  
|Biblioteca de Controle da Web|**Sim**|  
|Serviço do Windows|**Sim**|  
|Site|Não|  
  
## Consulte também  
 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>   
 <xref:System.ArgumentException>   
 [Acessando serviços Web do aplicativo](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)