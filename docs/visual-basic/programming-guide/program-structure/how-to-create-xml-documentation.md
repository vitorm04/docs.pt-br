---
title: Como criar documentação XML no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 7fb56da8a28367a6dcd5e28f208b4519510d7d95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Como criar documentação XML no Visual Basic
Este exemplo mostra como adicionar comentários de documentação XML a seu código.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>Para criar documentação XML para um tipo ou membro  
  
1.  No **Editor de códigos**, posicione o cursor na linha acima do tipo ou membro para o qual você deseja criar documentação.  
  
2.  Tipo `'''` (três aspas).  
  
     Um esqueleto XML para o tipo ou membro é adicionado a **Editor de código**.  
  
3.  Adicione informações descritivas entre as marcas apropriadas.  
  
    > [!NOTE]
    >  Se você adicionar linhas adicionais no bloco de documentação XML, cada linha deve começar com `'''`.  
  
4.  Adicione código adicional que usa o tipo ou membro com os novos comentários de documentação XML.  
  
     O IntelliSense exibe o texto do \<resumo > marca para o tipo ou membro.  
  
5.  Compile o código para gerar um arquivo XML que contém os comentários de documentação. Para obter mais informações, consulte [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
## <a name="see-also"></a>Consulte também  
 [Documentando o Código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
