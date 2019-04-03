---
title: 'Como: Criar documentação XML no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 2f32847c1b3a0fdf1892d6b423bb33783b6bdfe3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814582"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Como: Criar documentação XML no Visual Basic
Este exemplo mostra como adicionar comentários de documentação XML ao seu código.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>Para criar documentação XML para um tipo ou membro  
  
1.  No **Editor de códigos**, posicione o cursor na linha acima do tipo ou membro para o qual você deseja criar documentação.  
  
2.  Tipo `'''` (três aspas simples).  
  
     Um esqueleto XML para o tipo ou membro é adicionado a **Editor de códigos**.  
  
3.  Adicione informações descritivas entre as marcas apropriadas.  
  
    > [!NOTE]
    >  Se você adicionar linhas adicionais no bloco de documentação XML, cada linha deve começar com `'''`.  
  
4.  Adicione mais código que usa o tipo ou membro com os novos comentários de documentação XML.  
  
     O IntelliSense exibe o texto do \<resumo > marca para o tipo ou membro.  
  
5.  Compile o código para gerar um arquivo XML que contém os comentários de documentação. Para obter mais informações, consulte [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
## <a name="see-also"></a>Consulte também

- [Documentando o Código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
