---
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: 6ee842dbe65cbd9d147e77ec523a2b031d303738
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002395"
---
# <a name="-baseaddress"></a>-baseaddress
Especifica um endereço base padrão ao criar uma DLL.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`address`|Necessário. O endereço básico da DLL. Esse endereço deve ser especificado como um número hexadecimal.|  
  
## <a name="remarks"></a>Comentários  
 O endereço base padrão de uma DLL é definido pelo .NET Framework.  
  
 Lembre-se de que a palavra de ordem inferior nesse endereço é arredondada. Por exemplo, se você especificar 0x11110001, ele será arredondado para 0x11110000.  
  
 Para concluir o processo de assinatura de uma DLL, use a opção `–R` da ferramenta de nomeação forte (SN. exe).  
  
 Essa opção será ignorada se o destino não for uma DLL.  
  
|Para Set-BaseAddress no IDE do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Compilar**.<br />3.  Clique em **Avançadas**.<br />4.  Modifique o valor na caixa **endereço base do dll:** . **Observação:**      A caixa **endereço base de dll:** é somente leitura a menos que o destino seja uma dll.|  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Sn. exe (ferramenta Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md))
