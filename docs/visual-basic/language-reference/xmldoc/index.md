---
title: marcações XML recomendadas para comentários da documentação (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 2d6519af8ca1a0e2d59131eec4d63646dce7318b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913499"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>marcações XML recomendadas para comentários da documentação (Visual Basic)
O compilador Visual Basic pode processar comentários de documentação em seu código para um arquivo XML. Você pode usar ferramentas adicionais para processar o arquivo XML na documentação do.  
  
 Comentários XML são permitidos em construções de código, como tipos e membros de tipo. Para tipos parciais, apenas uma parte do tipo pode ter comentários XML, embora não haja nenhuma restrição ao comentar seus membros.  
  
> [!NOTE]
> Comentários de documentação não podem ser aplicados a namespaces. O motivo é que um namespace pode abranger vários assemblies, e nem todos os assemblies precisam ser carregados ao mesmo tempo.  
  
 O compilador processa qualquer marca que seja XML válida. As marcas a seguir fornecem funcionalidade comumente usada na documentação do usuário.  
  
||||  
|---|---|---|  
|[\<c>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> o compilador verifica a sintaxe.)  
  
> [!NOTE]
> Se você quiser que os colchetes angulares apareçam no texto de um comentário de `&lt;` documentação `&gt;`, use e. Por exemplo, a cadeia `"&lt;text in angle brackets&gt;"` de caracteres será `<text in angle brackets>`exibida como.  
  
## <a name="see-also"></a>Consulte também

- [Documentando o Código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Como: Criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
