---
title: Valor de soma de verificação incorreto, dígitos não hexadecimais ou número ímpar de dígitos hexadecimais
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: e682c2c23dd6fe80aee87d2a86b3df2dae66b802
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677494"
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

- [Visão geral do ASP.NET](/aspnet/overview)  
- [Fale conosco](/visualstudio/ide/talk-to-us)
