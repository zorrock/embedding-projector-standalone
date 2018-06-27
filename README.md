# embedding-projector-standalone

q.getCurrentState = function() {
    var a = new Sq.State;
    a.projections = [];
    for (var b = 0; b < this.dataSet.points.length; b++) {
        for (var c = this.dataSet.points[b], d = {}, e = Object.keys(c.projections), f = 0; f < e.length; ++f)
            d[e[f]] = c.projections[e[f]];
        a.projections.push(d)
    }


    tmpDataSet = this.dataSet.getSubset(this.selectedPointIndices);

    var text_all = '';
    tmpDataSet.points.map(function(item) {
        text_all += item.metadata['label'].toString() + '\n';
        //console.log(item.metadata['label'].toString());
    });
    console.log(text_all);

    $("#hehe").children().remove();
    $("#hehe").val(text_all);
    $('#hahahe', parent.document).children().remove();
    $('#hahahe', parent.document).val(text_all);

    $('#segButton', parent.document).click();

    a.selectedProjection = this.projection.projectionType;
    a.dataSetDimensions = this.dataSet.dim;
    a.tSNEIteration = this.dataSet.tSNEIteration;
    a.selectedPoints = this.selectedPointIndices;
    a.filteredPoints = this.dataSetFilterIndices;
    this.projectorScatterPlotAdapter.populateBookmarkFromUI(a);
    a.selectedColorOptionName = this.dataPanel.selectedColorOptionName;
    a.selectedLabelOption = this.selectedLabelOption;
    this.projectionsPanel.populateBookmarkFromUI(a);
    return a
}
;
