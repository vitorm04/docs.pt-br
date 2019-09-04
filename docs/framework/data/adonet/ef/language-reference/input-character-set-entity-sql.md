---
title: Conjunto de caracteres de entrada (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
ms.openlocfilehash: b1c6475704ec384800af0b678edd943246bf8044
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250633"
---
# <a name="input-character-set-entity-sql"></a>Conjunto de caracteres de entrada (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] aceita os caracteres de UNICODE codificados em UTF-16.  
  
 Literais de cadeia de caracteres podem conter qualquer caractere UTF-16 colocado entre aspas simples. Por exemplo, N'文字列リテラル. Quando os literais de cadeia de caracteres são comparados, os valores de original UTF-16 são usados. Por exemplo, N'ABC é diferente em páginas de código japonesas e latinos.  
  
 Comentários podem conter qualquer caractere UTF-16.  
  
 Os identificadores escapados podem conter qualquer caractere UTF-16 entre colchetes. Por exemplo, エスケープされた識別子 []. A comparação de identificadores escapados UTF-16 não difere maiúsculas de minúsculas. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] trata versões de letras que aparecem o mesmo mas é páginas diferentes de código como caracteres diferentes. Por exemplo, [ABC] é equivalente a [abc] se os caracteres correspondentes forem da mesma página de código. No entanto, se os mesmos dois identificadores forem de páginas de código diferentes, eles não serão equivalentes.  
  
 Espaço em branco é qualquer caractere de espaço em branco UTF-16.  
  
 Uma nova linha é qualquer caractere de nova linha UTF-16 normalizado. Por exemplo, “\ n” e “\ \ r em” é considerado caracteres de nova linha, mas “\ r” não é um caractere de nova linha.  
  
 Palavras-chave, as expressões, e pontuação podem ser qualquer caractere UTF-16 que normalizar ao latim. Por exemplo, SELECT em uma página de código japonesa é uma palavra-chave válida.  
  
 Palavras-chave, as expressões, e pontuação só podem ser caracteres latinos. `SELECT` em uma página de código japonesa não é uma palavra-chave. +,-, \*,/, =, (,), ', [,] e qualquer outra construção de linguagem não entre aspas aqui só pode ser caracteres latinos.  
  
 Os identificadores simples só podem ser caracteres latinos. Isso evita a ambiguidade durante a comparação, porque os valores originais são comparados. Por exemplo, ABC seria diferente nas páginas de código japonês e latino.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do Entity SQL](entity-sql-overview.md)
