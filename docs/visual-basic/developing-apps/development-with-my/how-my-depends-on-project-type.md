---
title: Como My depende do tipo de projeto (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: 989329da7dc57cd50b9ce6c88117152d0cb93d66
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775197"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>Como My depende do tipo de projeto (Visual Basic)
`My` expõe apenas os objetos exigidos por um determinado tipo de projeto. Por exemplo, o objeto `My.Forms` está disponível em um aplicativo Windows Forms, mas não está disponível em um aplicativo de console. Este tópico descreve quais objetos de `My` estão disponíveis em diferentes tipos de projeto.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>Meu nos aplicativos e sites do Windows  
 `My` expõe apenas os objetos que são úteis no tipo de projeto atual; Ele suprime objetos que não são aplicáveis. Por exemplo, a imagem a seguir mostra o modelo de objeto `My` em um projeto Windows Forms.  
  
 ![Diagrama que mostra o modelo de objeto My em um aplicativo Windows Forms.](./media/how-my-depends-on-project-type/my-object-model-windows-forms.png)  
  
 Em um projeto de site, `My` expõe objetos que são relevantes para um desenvolvedor da Web (como os objetos `My.Request` e `My.Response`) ao mesmo tempo em que suprimim objetos que não são relevantes (como o objeto `My.Forms`). A imagem a seguir mostra o modelo de objeto `My` em um projeto de site da Web:  
  
 ![Diagrama que mostra o modelo de objeto My em um aplicativo Web.](./media/how-my-depends-on-project-type/my-object-model-web.png)  
  
## <a name="project-details"></a>Detalhes do projeto  
 A tabela a seguir mostra quais `My` objetos estão habilitados por padrão para oito tipos de projeto: aplicativo do Windows, biblioteca de classes, aplicativo de console, biblioteca de controle do Windows, biblioteca de controle da Web, serviço do Windows, vazio e site da Web.  
  
 Há três versões do objeto `My.Application`, duas versões do objeto `My.Computer` e duas versões do `My.User` Object; os detalhes sobre essas versões são fornecidos nas notas de rodapé após a tabela.  
  
|Meu objeto|Aplicativo do Windows|Biblioteca de Classes|Aplicativo do Console|Biblioteca de controle do Windows|Biblioteca de controle da Web|Serviço do Windows|Vazio|Site da Web|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**Sim** <sup>1</sup>|**Sim** <sup>2</sup>|**Sim** <sup>3</sup>|**Sim** <sup>2</sup>|Não|**Sim** <sup>3</sup>|Não|Não|  
|`My.Computer`|**Sim** <sup>4</sup>|**Sim** <sup>4</sup>|**Sim** <sup>4</sup>|**Sim** <sup>4</sup>|**Sim** <sup>5</sup>|**Sim** <sup>4</sup>|Não|**Sim** <sup>5</sup>|  
|`My.Forms`|**Sim**|Não|Não|**Sim**|Não|Não|Não|Não|  
|`My.Log`|Não|Não|Não|Não|Não|Não|Não|**Sim**|  
|`My.Request`|Não|Não|Não|Não|Não|Não|Não|**Sim**|  
|`My.Resources`|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|Não|Não|  
|`My.Response`|Não|Não|Não|Não|Não|Não|Não|**Sim**|  
|`My.Settings`|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|Não|Não|  
|`My.User`|**Sim** <sup>6</sup>|**Sim** <sup>6</sup>|**Sim** <sup>6</sup>|**Sim** <sup>6</sup>|**Sim** <sup>7</sup>|**Sim** <sup>6</sup>|Não|**Sim** <sup>7</sup>|  
|`My.WebServices`|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|Não|Não|  
  
 <sup>1</sup> Windows Forms versão de `My.Application`. Deriva da versão do console (consulte a observação 3); Adiciona suporte para interação com as janelas do aplicativo e fornece o modelo de aplicativo Visual Basic.  
  
 <sup>2</sup> versão da biblioteca do `My.Application`. Fornece a funcionalidade básica necessária para um aplicativo: fornece membros para gravar no log do aplicativo e acessar informações do aplicativo.  
  
 <sup>3</sup> versão do Console do `My.Application`. Deriva da versão da biblioteca (consulte a observação 2) e adiciona membros adicionais para acessar os argumentos de linha de comando do aplicativo e as informações de implantação do ClickOnce.  
  
 <sup>4</sup> versão do Windows do `My.Computer`. Deriva da versão do servidor (consulte a observação 5) e fornece acesso a objetos úteis em um computador cliente, como o teclado, a tela e o mouse.  
  
 <sup>5</sup> versão do servidor do `My.Computer`. Fornece informações básicas sobre o computador, como o nome, o acesso ao relógio e assim por diante.  
  
 <sup>6</sup> versão do Windows do `My.User`. Esse objeto é associado à identidade atual do thread.  
  
 <sup>7</sup> versão da Web do `My.User`. Esse objeto é associado à identidade do usuário da solicitação HTTP atual do aplicativo.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Personalizando quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-definir (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [Objeto My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
- [Objeto My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
- [Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
