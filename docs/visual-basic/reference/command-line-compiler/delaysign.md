---
title: /delaysign | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: 19
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
ms.openlocfilehash: 59d4ec227286c20b2b4ecf749a91f0c4ee8d25ca
ms.lasthandoff: 03/13/2017

---
# <a name="delaysign"></a>/delaysign
Especifica se o assembly será assinado total ou parcialmente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Opcional. Use `/delaysign-` se você quiser um assembly totalmente assinado. Use `/delaysign+` se você deseja colocar a chave pública no assembly e reserva espaço para o hash assinado. O padrão é `/delaysign-`.  
  
## <a name="remarks"></a>Comentários  
 O `/delaysign` opção não tem nenhum efeito a menos que usado com [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) ou [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).  
  
 Quando você solicita um assembly totalmente assinado, o compilador mistura o arquivo que contém o manifesto (metadados de assembly) e sinaliza esse hash com a chave privada. A assinatura digital resultante é armazenada no arquivo que contém o manifesto. Quando um assembly é assinado com atraso, o compilador não calcular e armazenar a assinatura mas reserva espaço no arquivo para a assinatura pode ser adicionada posteriormente.  
  
 Por exemplo, usando `/delaysign+`, um desenvolvedor em uma organização pode distribuir versões de teste não assinado de um assembly que testadores podem se registrar com o cache de assembly global e usar. Quando o trabalho no assembly é concluído, a pessoa responsável pela chave privada da organização totalmente pode assinar o assembly. Este compartimentalização protege a chave privada da organização contra divulgação, permitindo que todos os desenvolvedores possam trabalhar em assemblies.  
  
 Consulte [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) para obter mais informações sobre como assinar um assembly.  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a>Para definir /delaysign no Visual Studio ambiente de desenvolvimento integrado  
  
1.  Tenha um projeto selecionado no **Solution Explorer**. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Clique o **assinatura** guia.  
  
3.  Defina o valor no **atrasar a assinatura somente** caixa.  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
