---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 6b4b69d227c857442de6857fac023090b3698e81
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004639"
---
# <a name="-win32icon"></a>-win32icon
Insere um arquivo. ico no arquivo de saída. Esse arquivo. ico representa o arquivo de saída no **Explorador de arquivos**.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`filename`|O arquivo. ico a ser adicionado ao arquivo de saída. Coloque o nome de arquivo entre aspas ("") se ele contiver um espaço.|  
  
## <a name="remarks"></a>Comentários  
 Você pode criar um arquivo. ico com o compilador de recursos do Microsoft Windows (RC). O compilador de recursos é invocado quando você compila C++ um programa Visual; um arquivo. ico é criado a partir do arquivo. rc. As opções `-win32icon` e `-win32resource` são mutuamente exclusivas.  
  
 Consulte [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) para fazer referência a um arquivo de recurso .NET Framework ou [-Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) para anexar um arquivo de recurso de .NET Framework. Consulte [-Win32Resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) para importar um arquivo. res.  
  
|Para definir-win32icon no IDE do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Aplicativo**.<br />3.  Modifique o valor na caixa **ícone** .|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `In.vb` e anexa um arquivo. ico, `Rf.ico`.  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
