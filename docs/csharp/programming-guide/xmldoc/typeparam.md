---
title: '&lt;typeparam&gt; – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 87629346238e92cf95141e72d79be37f8b11e48f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241808"
---
# <a name="lttypeparamgt-c-programming-guide"></a>&lt;typeparam&gt; (Guia de Programação em C#)
## <a name="syntax"></a>Sintaxe  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 O nome do parâmetro de tipo. Coloque o nome entre aspas duplas (" ").  
  
 `description`  
 Uma descrição do parâmetro de tipo.  
  
## <a name="remarks"></a>Comentários  
 A marca `<typeparam>` deve ser usada no comentário para um tipo genérico ou para uma declaração de método descrever um dos parâmetros de tipo. Adicione uma marca para cada parâmetro de tipo do tipo ou do método genérico.  
  
 Para obter mais informações, consulte [Genéricos](../../../csharp/programming-guide/generics/index.md).  
  
 O texto da marca `<typeparam>` será exibido no IntelliSense, o relatório Web de comentários sobre código da [Janela do Pesquisador de Objetos](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser).  
  
 Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
