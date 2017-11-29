---
title: /delaysign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6c42e351808281d90eafdb6e61a3f1736ef15c9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="delaysign"></a>/delaysign
Especifica se o assembly será assinado total ou parcialmente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Opcional. Use `/delaysign-` se você quiser um assembly totalmente assinado. Use `/delaysign+` se você deseja colocar a chave pública no assembly e reserva de espaço para o hash assinado. O padrão é `/delaysign-`.  
  
## <a name="remarks"></a>Comentários  
 O `/delaysign` opção não tem nenhum efeito a menos que usado com [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) ou [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).  
  
 Quando você solicita um assembly totalmente assinado, o compilador usa o hash no arquivo que contém o manifesto (metadados de assembly) e sinaliza esse hash com a chave particular. A assinatura digital resultante é armazenada no arquivo que contém o manifesto. Quando um assembly é assinado com atraso, o compilador não calcular e armazenar a assinatura, mas as reservas de espaço no arquivo de forma a assinatura pode ser adicionada posteriormente.  
  
 Por exemplo, usando `/delaysign+`, um desenvolvedor em uma organização pode distribuir versões de teste não assinado de um assembly que testadores podem registrar com o cache de assembly global e usar. Quando o trabalho no assembly é concluído, a pessoa responsável pela chave privada da organização totalmente pode assinar o assembly. Este compartimentalização protege a chave privada da organização contra divulgação, permitindo que todos os desenvolvedores possam trabalhar em assemblies.  
  
 Consulte [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) para obter mais informações sobre como assinar um assembly.  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a>Para definir /delaysign no Visual Studio ambiente de desenvolvimento integrado  
  
1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Clique na guia **Assinatura**.  
  
3.  Definir o valor no **atrasar a assinatura apenas** caixa.  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
