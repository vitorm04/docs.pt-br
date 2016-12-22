---
title: "Como My depende do tipo de projeto (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "_MYTYPE"
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como My depende do tipo de projeto (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`My` expõe apenas os objetos exigidos por um tipo de projeto específico.  Por exemplo, o objeto `My.Forms` está disponível em um aplicativo de Windows Forms mas não está disponível em um aplicativo de console.  Este tópico descreve quais objetos `My` estão disponíveis em diferentes tipos de projetos.  
  
## My em Aplicativos do Windows e Sites da Web  
 `My` expõe somente objetos que são úteis no tipo de projeto atual; ele suprime objetos que não são aplicáveis.  Por exemplo, a imagem a seguir mostra o modelo de objeto `My` em um projeto do Windows Forms.  
  
 ![Forma do meu em um aplicativo Windows Forms](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 Em um projeto de site, `My` expõe objetos que são relevantes para o desenvolvedor da Web \(como os objetos `My.Request` e `My.Response`\) enquanto suprime objetos que não são relevantes \(como o objeto `My.Forms`\).  A imagem a seguir mostra o modelo de objeto `My` em um projeto de site Web:  
  
 ![Forma do meu em um aplicativo da Web](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## Detalhes do projeto  
 A tabela a seguir mostra quais objetos `My` estão ativados como padrão para oito tipos de projeto: aplicativo do Windows, biblioteca de classes, aplicativo de console, biblioteca de controle do Windows, biblioteca de controle da Web, serviço do Windows, vazio, e site.  
  
 Existem três versões do objeto `My.Application`, duas versões do objeto `My.Computer`, e duas versões do objeto `My.User`; detalhes sobre essas versões são fornecidos nas notas de rodapé após a tabela.  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|Objeto My|Aplicativo do Windows|Biblioteca de Classe|Aplicativo de Console|Biblioteca de Controle do Windows|Biblioteca de Controle da Web|Serviço do Windows|Vazio|Site|  
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
  
 <sup>1</sup> Versão do `My.Application` de Formulários do Windows.  Deriva da versão do console \(Veja a nota 3\); adiciona suporte para interagir com janelas do aplicativo e fornece o modelo de aplicativo do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 <sup>2</sup> Versão de Biblioteca de `My.Application`.  Fornece a funcionalidade básica necessária por um aplicativo: fornece membros para gravar no log do aplicativo e acessar informações do aplicativo.  
  
 <sup>3</sup> Versão de Console do `My.Application`.  Deriva da versão da biblioteca \(consulte observação 2\), e adiciona membros adicionais para acessar argumentos de linhas de comando e informações de implantação do ClickOnce.  
  
 <sup>4</sup> Versão do Windows do `My.Computer`.  Deriva da versão do servidor \(consulte Observação 5\), e fornece acesso a objetos úteis em uma máquina cliente, como o teclado, tela, e mouse.  
  
 <sup>5</sup> Versão do servidor do `My.Computer`.  Fornece informações básicas sobre o computador, como o nome, acesso ao relógio e assim por diante.  
  
 <sup>6</sup> Versão do Windows do `My.User`.  Este objeto é associado com Identidade atual da thread.  
  
 <sup>7</sup> Versão Web do `My.User`.  Este objeto é associado com a identidade do usuário da solicitação HTTP atual do aplicativo.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.Logging.Log>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [Personalizando quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)   
 [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [Objeto My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)   
 [Objeto My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)   
 [Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)