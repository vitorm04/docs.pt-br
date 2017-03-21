---
title: Como My depende do tipo de projeto (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: d193dade94980f04b31605ea6fa968f9fa7d0ad6
ms.lasthandoff: 03/13/2017

---
# <a name="how-my-depends-on-project-type-visual-basic"></a>Como My depende do tipo de projeto (Visual Basic)
`My`expõe apenas os objetos exigidos por um tipo de projeto específico. Por exemplo, o `My.Forms` objeto está disponível em um aplicativo Windows Forms, mas não está disponível em um aplicativo de console. Este tópico descreve quais `My` objetos estão disponíveis em diferentes tipos de projeto.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>Meu Windows em Sites e aplicativos Web  
 `My`expõe somente objetos que são úteis no tipo de projeto atual; Ele suprime objetos que não são aplicáveis. Por exemplo, a imagem a seguir mostra o `My` modelo de objeto em um projeto do Windows Forms.  
  
 ![Forma de My em um aplicativo Windows Forms](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 Em um projeto de site da Web, `My` expõe objetos que são relevantes para o desenvolvedor da Web (como o `My.Request` e `My.Response` objetos) enquanto suprime objetos que não são relevantes (como o `My.Forms` objeto). A imagem a seguir mostra o `My` modelo de objeto em um projeto de site da Web:  
  
 ![Forma de My em um aplicativo Web](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## <a name="project-details"></a>Detalhes do projeto  
 A tabela a seguir mostra quais `My` objetos estão ativados por padrão para oito tipos de projeto: aplicativo do Windows, biblioteca de classes, aplicativo de console, biblioteca de controle do Windows, biblioteca de controle da Web, serviço do Windows, vazio e site da Web.  
  
 Há três versões do `My.Application` objeto, duas versões do `My.Computer` objeto e duas versões do `My.User` objeto; detalhes sobre essas versões são fornecidos nas notas de rodapé após a tabela.  
  
|Objeto My|Aplicativo do Windows|Biblioteca de Classes|Aplicativo do Console|Biblioteca de controle do Windows|Biblioteca de Controles da Web|Serviço do Windows|Vazio|Site|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**Yes** <sup>1</sup>|**Yes** <sup>2</sup>|**Yes** <sup>3</sup>|**Yes** <sup>2</sup>|Não|**Yes** <sup>3</sup>|Não|Não|  
|`My.Computer`|**Yes** <sup>4</sup>|**Yes** <sup>4</sup>|**Yes** <sup>4</sup>|**Yes** <sup>4</sup>|**Yes** <sup>5</sup>|**Yes** <sup>4</sup>|Não|**Yes** <sup>5</sup>|  
|`My.Forms`|**Sim**|Não|Não|**Sim**|Não|Não|Não|Não|  
|`My.Log`|Não|Não|Não|Não|Não|Não|Não|**Sim**|  
|`My.Request`|Não|Não|Não|Não|Não|Não|Não|**Sim**|  
|`My.Resources`|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|Não|Não|  
|`My.Response`|Não|Não|Não|Não|Não|Não|Não|**Sim**|  
|`My.Settings`|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|Não|Não|  
|`My.User`|**Yes** <sup>6</sup>|**Yes** <sup>6</sup>|**Yes** <sup>6</sup>|**Yes** <sup>6</sup>|**Yes** <sup>7</sup>|**Yes** <sup>6</sup>|Não|**Yes** <sup>7</sup>|  
|`My.WebServices`|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|Não|Não|  
  
 <sup>1</sup> versão dos Windows Forms do `My.Application`. Deriva da versão do console (veja a Observação 3); Adiciona suporte para interação com janelas do aplicativo e fornece o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] modelo de aplicativo.  
  
 <sup>2</sup> versão da biblioteca de `My.Application`. Fornece a funcionalidade básica necessitada para um aplicativo: fornece membros para gravar no log de aplicativo e acessar informações do aplicativo.  
  
 <sup>3</sup> versão do console do `My.Application`. Deriva da versão da biblioteca (consulte a Observação 2), e adiciona membros adicionais para acessar argumentos de linha de comando do aplicativo e informações de implantação do ClickOnce.  
  
 <sup>4</sup> versão do Windows `My.Computer`. Deriva da versão do servidor (consulte a Observação 5) e fornece acesso a objetos úteis em uma máquina cliente, como o teclado, tela e mouse.  
  
 <sup>5</sup> versão de servidor `My.Computer`. Fornece informações básicas sobre o computador, como o nome, acesso ao relógio e assim por diante.  
  
 <sup>6</sup> versão do Windows `My.User`. Este objeto é associado com a identidade do segmento atual.  
  
 <sup>7</sup> versão da web `My.User`. Este objeto é associado com a identidade do usuário da solicitação HTTP atual do aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer></xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.Logging.Log></xref:Microsoft.VisualBasic.Logging.Log>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User></xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [Personalizando quais objetos estão disponíveis em meu](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [/Define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)   
 [Objeto My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [Objeto My. Request](../../../visual-basic/language-reference/objects/my-request-object.md)   
 [Objeto My. Response](../../../visual-basic/language-reference/objects/my-response-object.md)   
 [Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
