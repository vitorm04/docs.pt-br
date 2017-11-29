---
title: "Valor de soma de verificação incorreto, dígitos não hexadecimais ou número ímpar de dígitos hexadecimais"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords: BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1158742c8eaa51bcbb5607795f16ae6c2b570db4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a>Valor de soma de verificação incorreto, dígitos não hexadecimais ou número ímpar de dígitos hexadecimais
Um valor de soma de verificação contém dígitos hexadecimais inválidos ou um número ímpar de dígitos.  
  
 Quando o ASP.NET gera um arquivo de origem do Visual Basic (extensão .vb), ele calcula uma soma de verificação e a coloca em um arquivo de origem oculto identificado por `#externalchecksum`. Um usuário também pode gerar um arquivo .vb para isso, mas é melhor deixar esse processo para uso interno.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42033  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Se o ASP.NET estiver gerando o arquivo de origem do Visual Basic, reinicie a compilação do projeto.  
  
2.  Se esse aviso persistir após a reinicialização, reinstale o ASP.NET e tente compilar novamente.  
  
3.  Se o aviso ainda persistir, ou se você não estiver usando o ASP.NET, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do ASP.NET](https://msdn.microsoft.com/library/4w3ex9c2.aspx)  
 [Fale conosco](/visualstudio/ide/talk-to-us)
