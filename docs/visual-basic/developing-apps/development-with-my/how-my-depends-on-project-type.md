---
title: Como My depende do tipo de projeto
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: 975b8feb001bcab22185be0a360b0512de099b79
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330274"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>Como My depende do tipo de projeto (Visual Basic)

`My`expõe somente os objetos exigidos por um tipo de projeto específico. Por exemplo, o `My.Forms` objeto está disponível em um aplicativo Windows Forms, mas não está disponível em um aplicativo de console. Este tópico descreve quais `My` objetos estão disponíveis em diferentes tipos de projeto.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>Meu nos aplicativos e sites do Windows  

 `My`expõe somente objetos que são úteis no tipo de projeto atual; Ele suprime objetos que não são aplicáveis. Por exemplo, a imagem a seguir mostra `My` o modelo de objeto em um projeto Windows Forms.  
  
 ![Diagrama que mostra o modelo de objeto My em um aplicativo Windows Forms.](./media/how-my-depends-on-project-type/my-object-model-windows-forms.png)  
  
 Em um projeto de site da `My` Web, o expõe objetos que são relevantes para um desenvolvedor da Web `My.Request` ( `My.Response` como os objetos e) ao mesmo tempo em que suprimim objetos que `My.Forms` não são relevantes (como o objeto). A imagem a seguir mostra `My` o modelo de objeto em um projeto de site da Web:  
  
 ![Diagrama que mostra o modelo de objeto My em um aplicativo Web.](./media/how-my-depends-on-project-type/my-object-model-web.png)  
  
## <a name="project-details"></a>Detalhes do projeto  

 A tabela a seguir mostra `My` quais objetos são habilitados por padrão para oito tipos de projeto: aplicativo do Windows, biblioteca de classes, aplicativo de console, biblioteca de controle do Windows, biblioteca de controle da Web, serviço do Windows, vazio e site.  
  
 Há três versões do `My.Application` objeto, duas versões do `My.Computer` objeto e duas versões do `My.User` objeto; os detalhes sobre essas versões são fornecidos nas notas de rodapé após a tabela.  
  
|Meu objeto|Aplicativo do Windows|Biblioteca de Classes|Aplicativo do Console|Biblioteca de controle do Windows|Biblioteca de controle da Web|Serviço do Windows|Vazio|Site|  
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
  
 <sup>1</sup> Windows Forms versão do `My.Application`. Deriva da versão do console (consulte a observação 3); Adiciona suporte para interação com as janelas do aplicativo e fornece o modelo de aplicativo Visual Basic.  
  
 <sup>2</sup> versão da biblioteca `My.Application`do. Fornece a funcionalidade básica necessária para um aplicativo: fornece membros para gravar no log do aplicativo e acessar informações do aplicativo.  
  
 <sup>3</sup> versão do console `My.Application`do. Deriva da versão da biblioteca (consulte a observação 2) e adiciona membros adicionais para acessar os argumentos de linha de comando do aplicativo e as informações de implantação do ClickOnce.  
  
 <sup>4</sup> versão do Windows `My.Computer`do. Deriva da versão do servidor (consulte a observação 5) e fornece acesso a objetos úteis em um computador cliente, como o teclado, a tela e o mouse.  
  
 <sup>5</sup> versão do servidor `My.Computer`do. Fornece informações básicas sobre o computador, como o nome, o acesso ao relógio e assim por diante.  
  
 <sup>6</sup> versão do Windows `My.User`do. Esse objeto é associado à identidade atual do thread.  
  
 <sup>7</sup> versão da Web `My.User`do. Esse objeto é associado à identidade do usuário da solicitação HTTP atual do aplicativo.  
  
## <a name="see-also"></a>Veja também

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Como personalizar quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-definir (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [Objeto My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
- [Objeto My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
- [Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
