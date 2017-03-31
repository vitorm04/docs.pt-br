---
title: "-delaysign (Opções do compilador do C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /delaysign
dev_langs:
- CSharp
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a22633027f07cf60f326417d22c2b3271a6f9cb9
ms.lasthandoff: 03/13/2017

---
# <a name="delaysign-c-compiler-options"></a>/delaysign (opções do compilador C#)
Essa opção faz com que o compilador reserve espaço no arquivo de saída para que uma assinatura digital possa ser adicionada mais tarde.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/delaysign[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Use **/delaysign-** se você quiser um assembly totalmente assinado. Use **/delaysign+** se você apenas deseja colocar a chave pública no assembly. O padrão é **/delaysign-**.  
  
## <a name="remarks"></a>Comentários  
 A opção **/delaysign** não tem nenhum efeito a menos que seja usada com [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) ou [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).  
  
 Quando você solicita um assembly totalmente assinado, o compilador usa o hash no arquivo que contém o manifesto (metadados de assembly) e sinaliza esse hash com a chave particular. A assinatura digital resultante é armazenada no arquivo que contém o manifesto. Quando um assembly é assinado com atraso, o compilador não calcula e armazena a assinatura, mas reserva o espaço no arquivo, de forma que a assinatura possa ser adicionada depois.  
  
 Por exemplo, o uso de **/delaysign+** permite que um testador coloque o assembly no cache global. Após o teste, é possível assinar completamente o assembly, colocando a chave particular no assembly com o utilitário [Assembly Linker](https://msdn.microsoft.com/library/c405shex).  
  
 Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](https://msdn.microsoft.com/library/xwb8f617) e [Atraso na Assinatura de um Assembly](http://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Modifique a propriedade **Apenas adiar a assinatura**.  
  
 Para obter informações sobre como definir essa opção do compilador de maneira programática, consulte <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB: como modificar as propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
