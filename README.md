# Acecraftusing UnityEngine;
using UnityEngine.UI;
using TMPro;

public class CharacterContestUI : MonoBehaviour {
    [Header("Contest Entry")]
    public AcecraftPilot pilot;
    public Image portrait;
    public TextMeshProUGUI nameText, callsignText, styleRankText, modeSIDText;
    public Slider contestScoreSlider;
    
    [Header("Paper Mario Style")]
    public Image background;
    public Animator flipAnimator;
    
    void Start() {
        RefreshDisplay();
    }
    
    public void RefreshDisplay() {
        nameText.text = pilot.pilotName;
        callsignText.text = pilot.callsign;
        styleRankText.text = GetStyleLetter(pilot.styleRank);
        modeSIDText.text = $"ICAO24: {pilot.modeS_ID:X6}";
        contestScoreSlider.value = pilot.styleRank / 100f;
    }
    
    string GetStyleLetter(int score) {
        if (score >= 100) return "S";
        if (score >= 75) return "A";
        if (score >= 50) return "B";
        return "D";
    }
    
    public void OnSubmitContest() {
        // Paper Mario-style "vote" animation
        flipAnimator.SetTrigger("Submit");
        Debug.Log($"iii Johnson Dalton submitted to contest! Score: {pilot.styleRank}");
    }
}
