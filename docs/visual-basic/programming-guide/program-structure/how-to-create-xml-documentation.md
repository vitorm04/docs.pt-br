---
title: "Como: criar documentação XML no Visual Basic | Documentos do Microsoft"
ms.custom: 
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
- XML comments
- XML documentation, creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 363a20c0fce05566b61e764d05932a9dfb779f90
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Como criar documentação XML no Visual Basic
Este exemplo mostra como adicionar comentários de documentação XML a seu código.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>Para criar documentação XML para um tipo ou membro  
  
1.  No **Editor de códigos**, posicione o cursor na linha acima do tipo ou membro para o qual você deseja criar documentação.  
  
2.  Tipo de `'''` (três aspas simples).  
  
     Um esqueleto XML para o tipo ou membro é adicionado a **Editor de código**.  
  
3.  Adicione informações descritivas entre as marcas apropriadas.  
  
    > [!NOTE]
    >  Se você adicionar linhas adicionais no bloco de documentação XML, cada linha deve começar com `'''`.  
  
4.  Adicione código adicional que usa o tipo ou membro com os novos comentários de documentação XML.  
  
     O IntelliSense exibe o texto do \<resumo > marca para o tipo ou membro.  
  
5.  Compile o código para gerar um arquivo XML contendo comentários de documentação. Para obter mais informações, consulte [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
## <a name="see-also"></a>Consulte também  
 [Documentar seu código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)   
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
