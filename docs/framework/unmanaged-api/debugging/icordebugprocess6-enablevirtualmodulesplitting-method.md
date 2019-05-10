---
title: Método ICorDebugProcess6::EnableVirtualModuleSplitting
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0f4a1de47670c59f2794feecd0be301a68b8724
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613806"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>Método ICorDebugProcess6::EnableVirtualModuleSplitting
Habilita ou desabilita a divisão de módulo virtual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `enableSplitting`  
 `true` para habilitar a divisão de módulo virtual; `false` para desabilitá-la.  
  
## <a name="remarks"></a>Comentários  
 Causas de divisão de módulo virtual [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) reconheça os módulos que foram mesclados durante a compilação, processam e apresentação-los como um grupo de módulos separados em vez de um único módulo grande. Isso altera o comportamento de vários [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) métodos descritos abaixo.  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
 Esse método pode ser chamado e o valor de `enableSplitting` pode ser alterado a qualquer momento. Não faz com que qualquer alteração funcionais de estado em um [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objeto, exceto alterar o comportamento dos métodos listados na [divisão de módulo Virtual e as APIs de depuração não gerenciadas](#APIs) seção no momento em que eles são chamados. Usar módulos virtuais provoca uma perda de desempenho ao chamar esses métodos. Além disso, o cache em memória significativa dos metadados virtualizados talvez precise implementar corretamente o [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) APIs e esses caches podem ser retidos mesmo após a divisão de módulo virtual foi desativada.  
  
## <a name="terminology"></a>Terminologia  
 Os seguintes termos são usados para descrever a divisão do módulo virtual:  
  
 módulos de contêiner ou contêineres  
 Os módulos agregados.  
  
 submódulos ou módulos virtuais  
 Os módulos encontrados em um contêiner.  
  
 módulos regulares  
 Módulos que não foram mesclados no tempo de compilação. Eles não são módulos de contêiner nem submódulos.  
  
 Módulos de contêiner e submódulos são representados por objetos de interface ICorDebugModule. No entanto, o comportamento da interface é ligeiramente diferente em cada caso, como o \<x-ref à seção > seção descreve.  
  
## <a name="modules-and-assemblies"></a>Módulos e assemblies  
 Vários assemblies de módulo não são suportados para cenários de mesclagem de assembly, portanto, há um relacionamento individual entre um módulo e um assembly. Cada objeto ICorDebugModule, independentemente se ele representa um módulo de contêiner ou um submódulo, possui um objeto de ICorDebugAssembly correspondente. O [icordebugmodule:: Getassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) método converte do módulo ao assembly. Para mapear na outra direção, o [icordebugassembly:: Enumeratemodules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md) método enumera apenas 1 módulo. Como o assembly e o module formam um par de ligação estreita nesse caso, os termos assembly e módulo se tornar sinônimos.  
  
## <a name="behavioral-differences"></a>Diferenças de comportamento  
 Módulos de contêiner têm as seguintes características e comportamentos:  
  
- Seus metadados para todos os submódulos constituintes é mesclado.  
  
- Seus nomes de tipos podem ser danificados.  
  
- O [icordebugmodule:: GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) método retorna o caminho para um módulo em disco.  
  
- O [icordebugmodule:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) método retorna o tamanho da imagem.  
  
- O método ICorDebugAssembly3.EnumerateContainedAssemblies lista os submódulos.  
  
- O método ICorDebugAssembly3.GetContainerAssembly retorna `S_FALSE`.  
  
 Submódulos têm as seguintes características e comportamentos:  
  
- Eles têm um conjunto reduzido de metadados que corresponde apenas ao assembly original que foi mesclado.  
  
- Os nomes de metadados não são danificados.  
  
- Os tokens de metadados dificilmente correspondem aos tokens do assembly original antes de ser mesclado no processo de compilação.  
  
- O [icordebugmodule:: GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) método retorna o nome do assembly, não um caminho de arquivo.  
  
- O [icordebugmodule:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) método retorna o tamanho original da imagem não mescladas.  
  
- O método ICorDebugModule3.EnumerateContainedAssemblies retorna `S_FALSE`.  
  
- O método ICorDebugAssembly3.GetContainerAssembly retorna o módulo recipiente.  
  
## <a name="interfaces-retrieved-from-modules"></a>Interfaces obtidas de módulos  
 Uma variedade de interfaces pode ser criada ou obtida de módulos. Algumas dessas incluem:  
  
- Um objeto ICorDebugClass, que é retornado pelo [icordebugmodule:: Getclassfromtoken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md) método.  
  
- Um objeto ICorDebugAssembly, que é retornado pelo [icordebugmodule:: Getassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) método.  
  
 Esses objetos sempre são armazenados em cache por [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md), e eles terão a mesma identidade de ponteiro, independentemente se eles foram criados ou consultados a partir do módulo de contêiner ou um submódulo. O submódulo fornece uma exibição filtrada desses objetos em cache, não um cache separado com suas própria cópias.  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Divisão do módulo virtual e APIs de depuração não gerenciadas  
 A tabela a seguir mostra como a divisão de módulo virtual afeta o comportamento de outros métodos na API de depuração não gerenciada.  
  
|Método|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Retorna o submódulo no qual essa função foi originalmente definida.|Retorna o módulo recipiente ao qual essa função foi mesclada.|  
|[ICorDebugClass::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Retorna o submódulo no qual essa classe foi originalmente definida.|Retorna o módulo recipiente ao qual essa classe foi mesclada.|  
|ICorDebugModuleDebugEvent::GetModule|Retorna o módulo recipiente que foi carregado. Submódulos não recebem eventos de carga independente dessa configuração.|Retorna o módulo recipiente que foi carregado.|  
|[ICorDebugAppDomain::EnumerateAssemblies](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Retorna uma lista de sub-assemblies e assemblies regulares; nenhum assembly contêiner está incluído. **Observação:**  Se qualquer assembly contêiner tiver símbolos ausentes, nenhum dos seus sub-assemblies será enumerado. Se qualquer assembly regular estiver com símbolos ausentes, ele pode ou não ser enumerado.|Retorna uma lista de assemblies recipientes e assemblies regulares; nenhum assembly contêiner está incluído. **Observação:**  Se qualquer assembly regular estiver com símbolos ausentes, ele pode ou não ser enumerado.|  
|[Icordebugcode:: Getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (para se referir a somente o código IL)|Retorna IL que seria válido em uma imagem de assembly pré-mesclagem. Especificamente, qualquer tokens de metadados embutido serão corretamente tokens TypeRef ou MemberRef quando os tipos sendo mencionados não são definidos no módulo virtual que contém o IL. Esses tokens TypeRef ou MemberRef podem ser pesquisados na [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) objeto para o objeto ICorDebugModule virtual correspondente.|Retorna o IL na imagem de assembly pós-mesclagem.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugProcess6](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
