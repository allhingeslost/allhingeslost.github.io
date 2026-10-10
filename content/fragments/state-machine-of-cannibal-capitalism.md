---
title: State Machine of Cannibal Capitalism
description:
aliases:
tags:
  - fragment
  - capitalism
draft: false
created: 2026-09-20T14:43
updated: 2026-10-10T18:13
---
```pseudocode
// ========================================================
// PROGRAM: The Infinite Machine (Corporate Metastasis)
// MOTTO: "Growth for the sake of growth is the ideology of the cancer cell."
// ========================================================

STRUCT PublicCorporation:
    PROPERTIES:
        finite_resources = 100.0        // Planet, biosphere, raw materials
        host_vitality    = 100.0        // Labor force, community wellbeing
        target_growth_rate = 0.08       // Mandatory quarter-over-quarter expansion
        quarterly_profits  = 10.0
        shareholder_satisfaction = 0.0  // Can never be permanently filled

FUNCTION RunEconomicEngine():
    
    // The loop cannot stop; stagnation is treated as death
    WHILE (shareholder_satisfaction < INFINITY):
        
        // --- 1. SET THE TARGET ---
        next_quarter_target = quarterly_profits * (1.0 + target_growth_rate)

        // --- 2. EXTRACT FROM THE HOST ---
        finite_resources = finite_resources - extract_natural_capital()
        host_vitality    = host_vitality - optimize_labor_efficiency()

        // --- 3. EXTERNALIZE THE COSTS ---
        // (Do not account for these on the balance sheet)
        dump_externalities(carbon, ecological_degradation, social_burnout)

        // --- 4. PRESERVE SHORT-TERM VALUATION ---
        IF (quarterly_profits < next_quarter_target):
            trigger_mass_layoffs(percentage = 10)
            deprecate_product_quality()
            execute_stock_buybacks()
        END IF

        // --- 5. METASTASIZE (EXPANSION) ---
        acquire_competitors_or_eliminate()
        lobby_for_deregulation()

        // --- 6. CHECK HOST VIABILITY ---
        IF (finite_resources <= 0 OR host_vitality <= 0):
            PRINT "CRITICAL ALERT: Host environment depleted."
            
            // The algorithm has no exit condition for ecological/social limits
            // It attempts one final pivot:
            financialize_remaining_ruins()
            
            SYSTEM_COLLAPSE()
            BREAK  // Forced termination by physical reality
        END IF

        quarterly_profits = next_quarter_target
        PRINT "Quarterly earnings beat expectations. Growth must continue."

    END WHILE

END FUNCTION
```

This is no finite state machine this runaway cancer train that eats itself.