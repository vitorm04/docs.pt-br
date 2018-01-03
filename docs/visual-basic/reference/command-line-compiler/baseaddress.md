---
title: /baseaddress
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1ad39acdec92667fbb0848a1c64c567b504dcb67
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="baseaddress"></a>/baseaddress
Especifica um endereço base padrão ao criar uma DLL.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/baseaddress:address  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`address`|Necessário. O endereço básico da DLL. Esse endereço deve ser especificado como um número hexadecimal.|  
  
## <a name="remarks"></a>Comentários  
 O endereço de base de uma DLL padrão é definido pelo [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
 Lembre-se de que a palavra de ordem inferior nesse endereço será arredondada. Por exemplo, se você especificar 0x11110001, ele é arredondado para 0x11110000.  
  
 Para concluir o processo de assinatura para uma DLL, use o `–R` opção da ferramenta de nomeação forte (Sn.exe).  
  
 Essa opção será ignorada se o destino não é uma DLL.  
  
|Para definir /baseaddress no IDE do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Compilar**.<br />3.  Clique em **Avançadas**.<br />4.  Modificar o valor de **endereço de base DLL:** caixa. **Observação:** o **endereço de base DLL:** caixa é somente leitura, a menos que o destino é uma DLL.|  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Sn.exe (ferramenta de nome forte)] [Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md))
