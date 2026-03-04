# LEO-NET Workshop Website

This is the Jekyll-based website for the LEO-NET (LEO Networking and Communication) workshop series. This guide provides comprehensive instructions for future workshop chairs to update content for new editions.

## Quick Start

To run this website locally, you need to have Ruby and Jekyll installed:

```bash
bundle install
bundle exec jekyll serve
```

Then, open your browser and go to `http://localhost:4000`.

## Site Architecture

The website uses Jekyll with a data-driven approach. Content is stored in YAML files (`_data/` directory) and rendered through HTML templates. This separation allows easy content updates without touching HTML code.

## Content Update Guide for Future Chairs

### 1. Basic Conference Information (`_data/conference.yml`)

**Used in:** All pages (header, footer, titles)

```yaml
title: The 3rd ACM Workshop on LEO Networking and Communication
location: Coimbra, Portugal
short_title: LEO-NET
year: 2025
dates: September 8th, 2025
submission_site: https://leonet25.hotcrp.com/
```

**What to update:**

- Change `title` for new workshop number (4th, 5th, etc.)
- Update `location` with new conference city/country
- Update `year` for new edition
- Update `dates` with new workshop date
- Update `submission_site` with new HotCRP URL

### 2. Important Dates (`_data/dates.yml`)

**Used in:** Homepage and CFP page date sections

```yaml
submission: June 3rd, 2025 (23:59:59 AoE) [hard]
notification: June 25th, 2025
camera_ready: July 23nd, 2025
```

**What to update:**

- All submission deadlines
- Use `<del>old date</del> new date` format for deadline extensions
- Add `<span style="color:red;">[hard]</span>` for final deadlines

### 3. Homepage Content (`_data/homepage.yml`)

**Used in:** Main landing page content and countdown timer

```yaml
paragraphs: [array of descriptive paragraphs]
additional_info: "Additional program information"
countdown_date: "2025-09-08T08:50:00+01:00" # Workshop start time
meta:
  description: "SEO description"
  keywords: "SEO keywords"
  authors: "Chair names for meta tags"
```

**What to update:**

- Update `countdown_date` with exact workshop start time in ISO format
- Modify `paragraphs` for workshop focus areas
- Update `meta` information for SEO

**⚠️ Countdown Timer:** The countdown automatically switches behavior:

- Before workshop day: Shows countdown to workshop start
- On workshop day: Shows "Workshop Day!" message
- Countdown is hardcoded in JavaScript to use the date from `homepage.yml`

### 4. Call for Papers (`_data/cfp.yml`)

**Used in:** CFP page content

Key fields that must be updated:

- `intro`: Array of introductory paragraphs
- `topics`: List of research topics (displayed in two columns)
- `submission_guidelines`: Array of submission requirements
- `contact`: Contact information for questions

### 5. Workshop Program (`_data/program.yml`)

**Used in:** Program page - most complex data structure

```yaml
sessions:
  - time: "08:50 - 09:00"
    title: "Workshop Starts + Welcome Address"
    type: "opening"
    chair: "Presentation by Chairs"

  - time: "09:00 - 10:00"
    title: "Keynote: Cloud above the clouds"
    type: "keynote"
    speaker:
      name: "Dr. Paulo Mendes"
      title: "Airbus Research"
      image: "img/speakers/Paulo-Mendes.jpeg"
      profile_url: "https://example.com"
    talk:
      title: "Talk title"
      abstract: "Talk abstract"

  - time: "10:00 - 11:00"
    title: "Technical Session 1"
    type: "technical_session"
    chair: "Session Chair Name"
    papers:
      - title: "Paper Title"
        authors: "Author Names (Affiliations)"
        url: "https://paper-url.com" # Leave empty if no URL
```

**Session types supported:**

- `opening`: Welcome/closing sessions
- `keynote`: Keynote presentations
- `technical_session`: Regular paper sessions
- `panel`: Panel discussions
- `break`: Coffee breaks and lunch

**What to update:**

- Add keynote speaker photos to `img/speakers/`
- Update all session times, titles, and chairs
- Add accepted papers with author information
- Include paper URLs when available (leave empty string if not)

### 6. Committee Information (`_data/chairs.yml` and `_data/committee.yml`)

**Used in:** Committee page

`_data/chairs.yml`:

```yaml
general_chairs:
  - firstname: Nitinder
    lastname: Mohan
    institution: Delft University of Technology, Netherlands
    website: https://www.nitindermohan.com/
```

`_data/committee.yml`:

```yaml
tpc:
  - name: "Committee Member Name"
    institution: "Institution, Country"
    website: "https://website.com" # Optional
```

### 7. Featured Topics (`_data/features.yml`)

**Used in:** Homepage feature grid (4 items displayed)

```yaml
- title: "Global Connectivity"
  description: "Description of the feature"
```

### 8. Previous Editions (`_data/previous_editions.yml`)

**Used in:** Previous editions page

Add new entry for current year after workshop completion:

```yaml
editions:
  - year: "2025"
    location: "Coimbra, Portugal"
    conference: "ACM SIGCOMM 2025"
    description: "Description of the 2025 edition"
    website: "https://leo-net-workshop.github.io/2025/"
    badge: "Current Edition" # or "Latest Edition"
```

### 9. Camera Ready Instructions (`_data/camera_ready.yml`)

**Used in:** Camera ready page

Update submission deadlines and any specific requirements for the new year.

## File Structure Overview

```
├── _data/                    # All content data (YAML files)
│   ├── conference.yml        # Basic conference info
│   ├── dates.yml            # Important dates
│   ├── homepage.yml         # Homepage content
│   ├── cfp.yml              # Call for papers
│   ├── program.yml          # Workshop program
│   ├── chairs.yml           # Workshop organizers
│   ├── committee.yml        # TPC members
│   ├── features.yml         # Homepage features
│   └── previous_editions.yml # Past workshops
├── _includes/               # Reusable HTML components
│   ├── header.html          # Main homepage header
│   ├── header-small.html    # Other pages header
│   └── footer.html          # Site footer
├── img/                     # Images and assets
│   └── speakers/            # Keynote speaker photos
├── css/                     # Stylesheets
├── *.html                   # Page templates
└── README.md                # This file
```

## Visual Elements and Cosmetic Features

### Countdown Timer

- Location: Homepage header
- Data source: `_data/homepage.yml` (`countdown_date`)
- Behavior: Automatically detects workshop day and adjusts display
- Styling: Space-themed with orbital animation

### Satellite Animation

- Location: All page headers
- Implementation: CSS-based satellite constellation animation
- Responsive: Adapts to different screen sizes

### Navigation

- Dynamic logo visibility on scroll
- Mobile-responsive hamburger menu
- Smooth scroll behavior for anchor links

## Testing Your Changes

1. **Local Development:**

   ```bash
   bundle exec jekyll serve
   ```

2. **Check All Pages:**

   - Homepage: Verify countdown, features, dates
   - CFP: Check submission guidelines and dates
   - Program: Verify all sessions display correctly
   - Committee: Ensure all links work
   - Previous Editions: Verify new edition appears

3. **Mobile Testing:**
   - Test navigation menu
   - Check countdown timer display
   - Verify program schedule formatting

## Common Updates for New Workshop Editions

### Immediate Updates (Before CFP):

1. Update `_data/conference.yml` with new year, location, dates
2. Update `_data/dates.yml` with new deadlines
3. Update `_data/homepage.yml` countdown date
4. Update `_data/chairs.yml` if organizers change
5. Add previous year to `_data/previous_editions.yml`

### Mid-Process Updates:

1. Update `_data/cfp.yml` if submission guidelines change
2. Extend deadlines in `_data/dates.yml` if needed
3. Update `_data/committee.yml` with TPC members

### Final Updates (After Acceptance):

1. Update `_data/program.yml` with complete schedule
2. Add keynote speaker photos to `img/speakers/`
3. Add paper URLs to `_data/program.yml` as available
4. Update `_data/camera_ready.yml` with specific instructions

## Notes for Future Chairs

- **Backup Strategy:** Keep previous year's data files as reference
- **Image Guidelines:** Keynote speaker photos should be 120x120px minimum, square format
- **URL Management:** Ensure all external links are current and working
- **SEO:** Update meta tags in `_data/homepage.yml` for better search visibility
- **Accessibility:** Maintain proper heading structure and alt text for images

## Deployment

The site is typically deployed using GitHub Pages or similar Jekyll hosting. Ensure all changes are committed to the main branch for automatic deployment.

## Support

For technical issues with the website structure, contact previous workshop chairs or refer to Jekyll documentation at https://jekyllrb.com/
