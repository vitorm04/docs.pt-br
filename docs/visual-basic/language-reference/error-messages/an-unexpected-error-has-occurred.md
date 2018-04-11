---
title: Ocorreu um erro inesperado porque não foi possível adquirir um recurso do sistema operacional obrigatório para a inicialização de instância única
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8969303d66e946d5579c6cca592b5701c4ebd632
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>Ocorreu um erro inesperado porque não foi possível adquirir um recurso do sistema operacional obrigatório para a inicialização de instância única
O aplicativo não pôde adquirir um recurso do sistema operacional necessário. Algumas das causas possíveis para esse problema são:  
  
-   O aplicativo não possui permissão para criar objetos nomeados do sistema operacional.  
  
-   O Common Language Runtime não tem permissões para criar arquivos de memória mapeada.  
  
-   O aplicativo precisa acessar um objeto do sistema operacional, mas outro processo o está usando.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se o aplicativo possui permissões suficientes para criar objetos nomeados do sistema operacional.  
  
2.  Verifique se o Common Language Runtime possui permissões suficientes para criar arquivos de memória mapeada.  
  
3.  Reinicie o computador para limpar qualquer processo que possa estar usando os recursos necessários para se conectar ao aplicativo da instância original.  
  
4.  Observe as circunstâncias sob as quais ocorreu o erro e chame o Microsoft Product Support Services  
  
## <a name="see-also"></a>Consulte também  
 [Página de Aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Noções básicas do depurador](/visualstudio/debugger/debugger-basics)  
 [Fale conosco](/visualstudio/ide/talk-to-us)
