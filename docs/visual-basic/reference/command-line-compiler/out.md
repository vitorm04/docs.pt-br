---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 6b005ac26e3fffad350cb4ce52f7757c9fff2ac1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005337"
---
# <a name="-out-visual-basic"></a>-out (Visual Basic)
Especifica o nome do arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`filename`|Necessário. O nome do arquivo de saída criado pelo compilador. Se o nome do arquivo contiver um espaço, coloque o nome entre aspas ("").|  
  
## <a name="remarks"></a>Comentários  
 Especifique o nome completo e a extensão do arquivo a ser criado. Se você não fizer isso, o arquivo. exe usará o nome do arquivo de código-fonte que contém o procedimento `Sub Main` e o arquivo. dll usará seu nome do primeiro arquivo de código-fonte.  
  
 Se você especificar um nome de arquivo sem uma extensão. exe ou. dll, o compilador adicionará automaticamente a extensão para você, dependendo do valor especificado para a opção de compilador `-target`.  
  
|Para definir no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Aplicativo**.<br />3.  Modifique o valor na caixa **nome do assembly** .|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` e cria o arquivo de saída `T2.exe`.  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
