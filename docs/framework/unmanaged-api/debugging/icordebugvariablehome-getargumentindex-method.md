---
title: ICorDebugVariableHome::GetArgumentIndex (método)
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentiIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20f65218928ee07d67ea742154469ac3cbea9241
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvariablehomegetargumentindex-method"></a>ICorDebugVariableHome::GetArgumentIndex (método)
Obtiene el índice de un argumento de función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetArgumentIndex(  
    [out] ULONG32* pArgumentIndex  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pArgumentIndex`  
 [out] Un puntero para el índice del argumento.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve los siguientes valores.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|La llamada al método devuelve un índice de argumento válido.|  
|`E_FAIL`|Actual [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instancia representa una variable local.|  
  
## <a name="remarks"></a>Comentarios  
 El índice del argumento se puede utilizar para recuperar los metadatos para este argumento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ICorDebugVariableHome (interfaz)](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
