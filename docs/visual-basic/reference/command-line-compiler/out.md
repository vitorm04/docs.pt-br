---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 234071d043b2649e2438ed20fe044fb89cdb9bf8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655883"
---
# <a name="-out-visual-basic"></a>-out (Visual Basic)
Especifica o nome do arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`filename`|Necessário. O nome do arquivo de saída que o compilador cria. Se o nome do arquivo contém um espaço, coloque o nome entre aspas ("").|  
  
## <a name="remarks"></a>Comentários  
 Especifique o nome completo e a extensão de arquivo a ser criado. Se você não fizer isso, o arquivo de .exe leva seu nome a partir do arquivo de código-fonte que contém o `Sub Main` procedimento e o arquivo. dll leva seu nome do primeiro arquivo de código-fonte.  
  
 Se você especificar um nome de arquivo sem uma extensão .exe ou. dll, o compilador adiciona automaticamente a extensão para você, dependendo do valor especificado para o `-target` opção de compilador.  
  
|Para definir - out no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Aplicativo**.<br />3.  Modificar o valor de **nome do Assembly** caixa.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` e cria o arquivo de saída `T2.exe`.  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-alvo (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
