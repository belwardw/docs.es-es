---
title: "ICorDebugRegisterSet2::GetRegisters (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2.GetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f9deccff09c255b339a22af711906baf23d7df9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="45067-102">ICorDebugRegisterSet2::GetRegisters (Método)</span><span class="sxs-lookup"><span data-stu-id="45067-102">ICorDebugRegisterSet2::GetRegisters Method</span></span>
<span data-ttu-id="45067-103">Obtiene el valor de cada registro (para la plataforma en la que se está ejecutando actualmente el código) especificado por la máscara de bits especificado.</span><span class="sxs-lookup"><span data-stu-id="45067-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45067-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="45067-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45067-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="45067-105">Parameters</span></span>  
 `maskCount`  
 <span data-ttu-id="45067-106">[in] El tamaño, en bytes, de la `mask` matriz.</span><span class="sxs-lookup"><span data-stu-id="45067-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="45067-107">[in] Una matriz de bytes, cada bit de los cuales corresponde a un registro.</span><span class="sxs-lookup"><span data-stu-id="45067-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="45067-108">Si el bit es 1, se recuperará el valor del registro correspondiente.</span><span class="sxs-lookup"><span data-stu-id="45067-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="45067-109">[in] El número de valores de registro va a recuperar.</span><span class="sxs-lookup"><span data-stu-id="45067-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="45067-110">[out] Una matriz de `CORDB_REGISTER` objetos, cada uno de los cuales recibe el valor de un registro.</span><span class="sxs-lookup"><span data-stu-id="45067-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45067-111">Comentarios</span><span class="sxs-lookup"><span data-stu-id="45067-111">Remarks</span></span>  
 <span data-ttu-id="45067-112">El `GetRegisters` método devuelve una matriz de valores de los registros especificados por la máscara.</span><span class="sxs-lookup"><span data-stu-id="45067-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="45067-113">La matriz no contiene valores de registros cuyo bit de máscara no está establecido.</span><span class="sxs-lookup"><span data-stu-id="45067-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="45067-114">Por lo tanto, el tamaño de la `regBuffer` matriz debe ser igual al número de valores 1 en la máscara.</span><span class="sxs-lookup"><span data-stu-id="45067-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="45067-115">Si el valor de `regCount` es demasiado pequeño para el número de registros indicado por la máscara, los valores de los registros con números superior se truncará del conjunto.</span><span class="sxs-lookup"><span data-stu-id="45067-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="45067-116">Si `regCount` es demasiado grande, el sin usar `regBuffer` elementos estará sin modificar.</span><span class="sxs-lookup"><span data-stu-id="45067-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="45067-117">Si un registro no disponible se indica mediante la máscara, se devolverá un valor indeterminado para ese registro.</span><span class="sxs-lookup"><span data-stu-id="45067-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="45067-118">El `ICorDebugRegisterSet2::GetRegisters` método es necesario para plataformas que tengan más de 64 registros.</span><span class="sxs-lookup"><span data-stu-id="45067-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms which have more than 64 registers.</span></span> <span data-ttu-id="45067-119">Por ejemplo, IA64 tiene 128 registros de propósito general y 128 registros de punto flotante, por lo que tiene más de 64 bits en la máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="45067-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64-bits in the bit mask.</span></span>  
  
 <span data-ttu-id="45067-120">Si no tiene más de 64 registros, como es el caso en plataformas como x86, la `GetRegisters` método realmente se limita a traducir los bytes en el `mask` matriz de bytes en un `ULONG64` y, a continuación, llama a la [ICorDebugRegisterSet:: GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) método, que toma el `ULONG64` máscara.</span><span class="sxs-lookup"><span data-stu-id="45067-120">If you do not have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method actually just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45067-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45067-121">Requirements</span></span>  
 <span data-ttu-id="45067-122">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45067-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45067-123">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45067-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45067-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45067-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45067-125">**Versiones de .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45067-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45067-126">Vea también</span><span class="sxs-lookup"><span data-stu-id="45067-126">See Also</span></span>  
 [<span data-ttu-id="45067-127">ICorDebugRegisterSet2 (interfaz)</span><span class="sxs-lookup"><span data-stu-id="45067-127">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [<span data-ttu-id="45067-128">ICorDebugRegisterSet (interfaz)</span><span class="sxs-lookup"><span data-stu-id="45067-128">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)