---
title: Ocorreu um erro inesperado porque não foi possível adquirir um recurso do sistema operacional obrigatório para a inicialização de instância única
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 9643d14b3e94e814c492b362b9db3e37cff4ce9f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197376"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>Ocorreu um erro inesperado porque não foi possível adquirir um recurso do sistema operacional obrigatório para a inicialização de instância única
O aplicativo não pôde adquirir um recurso do sistema operacional necessário. Algumas das causas possíveis para esse problema são:  
  
- O aplicativo não possui permissão para criar objetos nomeados do sistema operacional.  
  
- O Common Language Runtime não tem permissões para criar arquivos de memória mapeada.  
  
- O aplicativo precisa acessar um objeto do sistema operacional, mas outro processo o está usando.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique se o aplicativo possui permissões suficientes para criar objetos nomeados do sistema operacional.  
  
2. Verifique se o Common Language Runtime possui permissões suficientes para criar arquivos de memória mapeada.  
  
3. Reinicie o computador para limpar qualquer processo que possa estar usando os recursos necessários para se conectar ao aplicativo da instância original.  
  
4. Observe as circunstâncias sob as quais ocorreu o erro e chame o Microsoft Product Support Services  
  
## <a name="see-also"></a>Consulte também

- [Página de Aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Noções básicas do depurador](/visualstudio/debugger/debugger-basics)
- [Fale conosco](/visualstudio/ide/feedback-options)
