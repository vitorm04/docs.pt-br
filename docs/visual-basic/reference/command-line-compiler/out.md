---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 67366e13e4dceea4772d0730222413cb25b4e8b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352381"
---
# <a name="-out-visual-basic"></a>-out (Visual Basic)
Especifica o nome do arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Argumentos  
  
|Termo|Definição|  
|---|---|  
|`filename`|Necessária. O nome do arquivo de saída criado pelo compilador. Se o nome do arquivo contiver um espaço, coloque o nome entre aspas ("").|  
  
## <a name="remarks"></a>Comentários  
 Especifique o nome completo e a extensão do arquivo a ser criado. Se você não fizer isso, o arquivo. exe usará o nome do arquivo de código-fonte que contém o procedimento `Sub Main`, e o arquivo. dll usará o nome do primeiro arquivo de código-fonte.  
  
 Se você especificar um nome de arquivo sem uma extensão. exe ou. dll, o compilador adicionará automaticamente a extensão para você, dependendo do valor especificado para a opção de compilador `-target`.  
  
|Para definir no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1. ter um projeto selecionado em **Gerenciador de soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2. Clique na guia **aplicativo** .<br />3. modifique o valor na caixa **nome do assembly** .|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` e cria `T2.exe`de arquivo de saída.  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
