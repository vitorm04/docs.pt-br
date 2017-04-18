---
title: "Todas as larguras de campo, exceto o último elemento, devem ser maiores que zero | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrTextFieldParser_FieldWidthsMustPositive
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8c2edd3d4b178b21f92c5e160c20e472389244ca
ms.lasthandoff: 03/13/2017

---
# <a name="all-field-widths-except-the-last-element-must-be-greater-than-zero"></a>Todas as larguras de campo, exceto o último elemento, devem ser maiores que zero
Todas as larguras de campo, exceto o último elemento, devem ser maiores que zero. Uma largura de campo que menor ou igual a zero no último elemento indica que o último campo é de comprimento variável.  
  
 A operação falhou porque uma largura de campo que não seja o último elemento está definida como zero ou menos. Uma largura de campo que menor ou igual a zero pode ser usado como o último elemento para indicar que o último campo é de comprimento variável, mas não pode ser usada como qualquer outro elemento.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Defina a largura do campo para o comprimento correto.  
  
## <a name="see-also"></a>Consulte também  
 [Método TextFieldParser.SetFieldWidths](http://msdn.microsoft.com/en-us/958fed9f-e0f3-4fc5-83b4-386156bdf036)   
 [Propriedade TextFieldParser.FieldWidths](http://msdn.microsoft.com/en-us/c6985360-60c6-494e-89e7-43b6b73f2597)   
 [Como: ler arquivos de texto de largura fixa](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [Objeto TextFieldParser](../../visual-basic/language-reference/objects/textfieldparser-object.md)
