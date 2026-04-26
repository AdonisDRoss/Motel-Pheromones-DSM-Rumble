STATE MACHINE
enum CombatState {
    IDLE,
    MOVE,
    ATTACK,
    HITSTUN,
    DASH,
    GRAB,
    KO,
    GROOVE
}
MOVE STRUCTURE
struct Move {
    string name;

    float startup;
    float active;
    float recovery;

    float damage;
    float knockback;

    bool canCancel;
    bool isSpecial;

    Hitbox[] hitboxes;
}

COMBO SYSTEM
if (timeSinceLastHit < 0.35f)
    comboActive = true;
else
    resetCombo();


DAMAGE SCALING
damage *= (1 - comboCount * 0.05f);

HIT DETECTION
if (hitbox.Intersects(hurtbox))
{
    ApplyDamage();
    ApplyKnockback();
    ApplyHitstun();
}



