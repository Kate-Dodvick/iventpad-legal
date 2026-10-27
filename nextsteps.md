# Production Launch Checklist

## Phase 1: DB Migration
- [ ] Export schema, functions, and policies from Dev DB.
- [ ] Create new `iventpad-prod` Supabase project.
- [ ] Run exported SQL in new Prod DB.
- [ ] Recreate storage buckets (event-covers, profile-photos).
- [ ] Update `eas.json` production profile with Prod keys.

## Phase 2: Play Console Setup
- [ ] Pay $25 Developer fee & verify ID.
- [ ] Create app in Play Console.
- [ ] Upload App Icon (512x512), Feature Graphic (1024x500), 4+ Screenshots.
- [ ] Write Short & Full descriptions (SEO optimized).
- [ ] Fill Data Safety form.
- [ ] Fill Content Rating form (Target: 18+).
- [ ] Link Privacy Policy URL.
- [ ] Create Reviewer Test Account (and populate with data).

## Phase 3: Closed Testing
- [ ] Build production `.aab` via EAS.
- [ ] Upload to Closed Testing track.
- [ ] Recruit 12–20 testers.
- [ ] Send Opt-in URL to testers.
- [ ] Monitor for 14 continuous days.

## Phase 4: Launch
- [ ] Apply for Production access (Day 15).
- [ ] Wait for Google review.
- [ ] Staged rollout (10% -> 50% -> 100%).
- [ ] Monitor Android Vitals for crashes.
